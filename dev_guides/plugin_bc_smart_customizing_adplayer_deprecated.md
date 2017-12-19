# Customizing the AdPlayer

The following variables can be added to Player-Level Key/Value Pairs in order to customise your Ooyala Ad Player.

|Key|Value|
|---|-----|
|vpHost|http://\{your-unique-subdomain\}.videoplaza.tv|
|vpTags|comma,separated,player,description|
|vpCategory|ContentHierarchyNodeID|
|vpContentPartner|ContentPartnerID|
|vpLongFormLimit|Set the value in seconds to define the threshold for short form content versus long form content|

Consult the [Flashvars](integration_flashvars_configuration_variables.md) article for additional configuration parameters.

## Example Configuration

`vpHost=http://vp-validation.videoplaza.tv;vpCategory=validation;vpTags=standard;`

**Parent topic:**[\(Deprecated\) Brightcove SMART Plugin \(Flash+HTML5\)](../../../oadtech/ad_serving/dg/plugin_bc_smart_flash_html5_deprecated.md)

