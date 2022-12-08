# Mainroad Theme Customization

https://onlinepngtools.com/. - great simple editing tools

https://imageoptim.com/howto.html - Image optimization

## Colours

* Britannia blue:  #0185C1
* Britannia yellow: #FEEF4D

## Fonts I like

[yawpitchroll/frugal](https://github.com/yawpitchroll/frugal) - Theme with nice fonts

[Font Stack](https://www.lifewire.com/font-stack-definition-3467414#:~:text=A%20font%20stack%20is%20a,as%20a%20font%20not%20loading.)

## Ideas from highway theme

* [CodingNConcepts Site](https://codingnconcepts.com/) and [Highway Theme github](https://github.com/ashishlahoti/hugo-theme-highway)

* The "social" widget and icons is quite nice... try to incorporate into mainroad2
  * Requires using widget/social.html, customizing it to add Strava support
  * Copying all the .css styling for:
    * "Social Widget"
    * "Social Share Buttons"
    * and adding Strava support in the Social Share Buttons styling
* The thumbnail icon is properly sized in highway... its way too big in mainroad
  * Copy the .css styling ".post__thumbnail" and ".post__thumbnail img" (for display of thumbnails in the post itself), and edit to display a reasonable size
  * Copy the .css styling ".list__thumbnail" and ".list__thumbnail img"  (for display of thumbnails in a list of posts), and edit to display a reasonable size
  * The thumbnail needs to be moved into the header of the single.html template
    * Copy mainroad defaults/single.html and modify the header to use the highway code
    * Copy the .css styling for "Posts/Pages -> .post__header, .main__header"
    * Check the post__thumbnail, post__lead, post_meta, and meta styling
* The [socialshare](https://codingnconcepts.com/hugo/social-icons-hugo/) feature is well documented.
* The [client side search](https://codingnconcepts.com/hugo/client-side-search-engine-hugo/) is also well documented

* The highway theme seems to have customization issues... it does not follow the same customization as mainroad. For example, the logo does not work
* There is minimal documentation for the highway theme. The example site has the TOML
* There seem to be minor bugs in the layout. The styling is 100% hard-coded CSS.
* The .css file in static is ignored.. the one in assets is used.
