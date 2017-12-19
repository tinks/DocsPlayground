# Adding the Ad Player to Your Video Player

In this video we explain how to create the Videoplaza class and how to integrate it into your video player.

\[ooyala:ZycXB0dTrRu8\_zZswAlCRiEJKA-cXZSk\]



**Videoplaza.as**

```
package {

  import com.videoplaza.api.utils.ItemInfo;
  import com.videoplaza.bridge.core.VideoplazaLoader;
  import com.videoplaza.bridge.core.VpAdPlayer;
  import com.videoplaza.bridge.events.PlayerState;
  import com.videoplaza.bridge.utils.IVideoplazaPlugin;

  import flash.display.Sprite;
  import flash.display.Stage;
  import flash.display.StageDisplayState;
  import flash.events.Event;

  import org.osmf.containers.MediaContainer;
  import org.osmf.events.AudioEvent;
  import org.osmf.events.MediaPlayerStateChangeEvent;
  import org.osmf.events.TimeEvent;
  import org.osmf.media.MediaPlayer;
  import org.osmf.traits.PlayState;

  public class Videoplaza extends Sprite implements IVideoplazaPlugin {

    private var _main:Player;
    private var _videoPlayer:MediaPlayer;
    private var _mediaContainer:MediaContainer;
    private var _videoPosition:Number;
    private var _vpAdPlayer:VpAdPlayer;
    private var _startNewAdSection:Boolean = true;

    private var _stage:Stage;

    private var _prevHeight:Number = NaN;
    private var _prevWidth:Number = NaN;

    public function Videoplaza() {
    }

    public function init(main:Player):void {
      _main = main
      _videoPlayer = main.videoPlayer;
      _mediaContainer = main.mediaContainer;
      _stage = main.mediaContainer.stage;

      //load ad player SDK from CDN
      var vpLoader:VideoplazaLoader = new VideoplazaLoader();
      vpLoader.init(this);
    }

    //********************************************
    //********** AD PLAYER INTERFACE ************
    //********************************************

    /**
    * FAIL: Start the videoplayer without ad player
    */
    public function videoplazaLoadedFail(errorMessage:String):void {
      //tell the player to start without ad player
      _videoPlayer.dispatchEvent(new Event('videoplazaFail'));
    }

    /**
    * SUCCESS: Add ad player to the stage
    */
    public function videoplazaLoadedSuccess(vpAdPlayer:VpAdPlayer):void {
      _vpAdPlayer = vpAdPlayer;
      getStage().addChild(_vpAdPlayer);

      setupVideoPlayerListeners();

      _prevWidth = _mediaContainer.width;
      _prevHeight = _mediaContainer.height;

      //if autoplay, start a new ad section straightaway
      if (_main.isAutoPlay) {
        _startNewAdSection = false;
        setNewItem();
        _vpAdPlayer.setPlayerState(PlayerState.PAUSED);
      }

      //tell the video player that the ad player is ready, now you can start!
      _videoPlayer.dispatchEvent(new Event('videoplazaReady'));
    }

    /**
    * REQUEST NEW AD SECTION: here we pass the configuration for the
    * request using the itemInfo object, _vpAdPlayer.setNewItem will trigger
    * a new HTTP request to the backend and get a JSON/XML response
    * containing ads.
    * 
    * @param media = a reference to the current media object
    */
    public function setNewItem(media:Object = null):void {
      var videoplazaConfig:Object = _stage.loaderInfo.parameters;

      var itemInfo:ItemInfo = new ItemInfo();
      itemInfo.category = (videoplazaConfig.vpcategory) ? videoplazaConfig.vpcategory : '';
      itemInfo.tags = (videoplazaConfig.vptags) ? videoplazaConfig.vptags.split(',') : [];

      _vpAdPlayer.setNewItem(temInfo);
    }

    /**
    * Every time a new ad module is created it will fire this method, this can be
    * used to add further costumizations and listeners to the ad modules.
    */
    public function onAdModuleCreated(moduleEvent:Event):void {
    }

    //********************************************
    //********** PLAYER EVENT LISTENERS **********
    //********************************************

    private function setupVideoPlayerListeners():void {
      _videoPlayer.addEventListener(MediaPlayerStateChangeEvent.MEDIA_PLAYER_STATE_CHANGE, meHandler);

      _videoPlayer.addEventListener(AudioEvent.MUTED_CHANGE, audioEventHandler);
      _videoPlayer.addEventListener(AudioEvent.VOLUME_CHANGE, audioEventHandler);

      _videoPlayer.addEventListener(TimeEvent.COMPLETE, timeEventHandler);
      _videoPlayer.addEventListener(TimeEvent.CURRENT_TIME_CHANGE, timeEventHandler);
      _videoPlayer.addEventListener(TimeEvent.DURATION_CHANGE, timeEventHandler);

      getStage().addEventListener(Event.RESIZE, stageEventHandler);
    }

    private function meHandler(e:MediaPlayerStateChangeEvent):void {
      switch(e.state) {
        case PlayState.PLAYING:
          //stop multiple ad call requests being made at the same time
          if (_startNewAdSection) {
            _videoPlayer.stop();
            _startNewAdSection = false;
            setNewItem();
          }
          _vpAdPlayer.setPlayerState(PlayerState.PLAYING);
          break;
        case PlayState.STOPPED:
          _vpAdPlayer.setPlayerState(PlayerState.PAUSED);
          break;
        case PlayState.PAUSED:
          _vpAdPlayer.setPlayerState(PlayerState.PAUSED);
          break;
      }
    }

    private function audioEventHandler(e:AudioEvent):void {
      _vpAdPlayer.setPlayerState(PlayerState.VOLUME_CHANGE);
    }

    private function timeEventHandler(e:TimeEvent):void {
      switch(e.type) {
        case TimeEvent.CURRENT_TIME_CHANGE:
          _videoPosition = e.time;
          break;
        case TimeEvent.DURATION_CHANGE:
          //tell the ad player as soon the duration metadata arrives
          var meta:Object = new Object();
          meta.duration = e.time;
          if (meta.duration)
            _vpAdPlayer.setMetaData(meta);
          break;
        case TimeEvent.COMPLETE:
          _vpAdPlayer.setPlayerState(PlayerState.CLIP_COMPLETE);
          _startNewAdSection = true;
          break;
      }
    }

    private function stageEventHandler(e:Event):void {
      _vpAdPlayer.setPlayerState(PlayerState.RESIZE);
    }

    //********************************************
    //*************** GET/SET ********************
    //********************************************

    public function get videoplazaConfig():Object {
      return _stage.loaderInfo.parameters;
    }

    public function get isMuted():Boolean {
      return _videoPlayer.muted;
    }

    public function get isFullScreen():Boolean {
      return (getStage>().displayState == StageDisplayState.FULL_SCREEN) ? true : false;
    }

    public function getStage():Stage {
      return _mediaContainer.stage;
    }

    public function getScreenX():Number {
      return _mediaContainer.x;
    }

    public function getScreenY():Number {
      return _mediaContainer.y;
    }

    public function getScreenWidth():Number {
      var width:Number;
      if (isFullScreen)
        width = getStage().fullScreenWidth;
      else if (_prevWidth)
        width = _prevWidth;  //fix for OSMF giving old size values
      else
        width = _mediaContainer.width;
      return width;
    }

    public function getScreenHeight():Number{
      var height:Number;

      if (isFullScreen)
        height = getStage().fullScreenHeight;
      else if (_prevHeight)
        height = _prevHeight; //fix for OSMF giving old size values
      else
        height = _mediaContainer.height;
      return height;
    }

    public function getPlayerVolume():Number {
      return _videoPlayer.volume;
    }

    public function getVideoPosition():Number {
      return _videoPosition;
    }

    public function setScreenPosition(x:Number, y:Number):void {
      _mediaContainer.x = x;
      _mediaContainer.y = y;
    }

    public function setScreenSize(w:Number,h:Number):void {
      _mediaContainer.width = w;
      _mediaContainer.height = h;
    }

    public function setPlayerVolume(volume:Number):void {
      _videoPlayer.volume = volume;
    }

    public function setPlayerPlay():void {
      _videoPlayer.play();
    }

    public function setPlayerPause():void {
      _videoPlayer.pause();
    }

    public function setPlayerControlsEnable(enable:Boolean):void {
      if (enable) {
        _videoPlayer.dispatchEvent(new Event('enableControlbar'));
      }
      else {
        _videoPlayer.dispatchEvent(new Event('disableControlbar'));
      }
    }

    /**
    * Expose the ad player so other classes in your player can listen or manipulate
    * the ad player object
    */
    public function get adPlayer():VpAdPlayer {
      return _vpAdPlayer;
    }
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

