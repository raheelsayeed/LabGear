# LabGear URL-based API

### For app-version 3.0 & up


**Note**: `labgear://` scheme works in all versions but the **`x-callback-url`** protocol is supported only in version 3.0 & up. To check if the installed LabGear app supports `x-callback-url`, a `[ .. canOpenURL]` call can be made to `x-labgear://`


----------


###X-Callback-URL:

X-Callback-URL(and its parameters) Remain optional. LabGear will function as expected without any of those.

    labgear://x-callback-url/[action]?[parameters]&[x-callback-parameters]

## Actions

### Lab Detail

 - **`lab`** - Viewing a Lab Test.
 - Params: `id` (Lab Identifier, string)
 - Eg. `labgear://x-callback-url/lab?id=SAAG`

### Filter

 - **`lablist`** - Lists an array of Lab tests (in the Main App View)
 - Param: `tags` (Lab Short-Abbreviation separated by a comma, string)
 - Eg. `labgear://x-callback-url/lablist?tags=Alb,Glu`
 - Param: ids (Lab identifiers separated by a comma)
 - Eg. `labgear://x-callback-url/lablist?ids=SAAG,PT`
 - **Note**: `tags` param will take precedence over `ids` if both are present.


### Notes


 - **`notes`** - Adds a string as a note to the lab).
 - Params: `text` (URL Encoded string).
 - Optional Param: `id` (Lab Identifier)
 - Eg. `labgear://x-callback-url/notes?text=SAAG%20is%20low%20in%20leukemias&id=SAAG`    (This will add the note to the lab with identifier SAAG.
 - **Note**: If No `id` parameter is present, LabGear will switch to *Search & Select* mode where the user will *search* and *select* the labs to which the Note will be added. 


### Optional Parameters (x-callback-url)

 - `x-success` (optional, URL): called after successfully adding Notes.
 - `x-cancel` (optional, URL): called when User taps 'Cancel'. It is not applicable when `id=` param is supplied.
 - `x-error` (optional, URL): called when `text=nil` or `id=nil` or `id` failed to identify a Lab test.
 - Eg. `labgear://x-callback-url/notes?text=&x-success=twitter:&x-cancel=medcalc:&x-error=medcalc:`
