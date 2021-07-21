To add new icons to the Wagtail icon font:

* go to https://icomoon.io/app/
* hamburger menu -> Manage project -> Import project
* open [wagtail/admin/static_src/wagtailadmin/fonts/wagtail-icomoon.json](https://github.com/wagtail/wagtail/blob/main/wagtail/admin/static_src/wagtailadmin/fonts/wagtail-icomoon.json)
* Rename 'Untitled Project 1' to 'Wagtail'
* click 'Load', Add icons from library, Font Awesome -> Add
* Select the icon(s) you want, then from the hamburger menu next to Wagtail, 'Copy selection to set'. Using the 'move' tool, move it to the end of the list
* From the hamburger menu next to Wagtail, 'select all', then 'Generate font'. Make a note of the hex code for the icon(s) you've added, and then click 'Download'.
* Unpack the zip file, and copy the `.woff` file in the 'fonts' folder to wagtail/admin/static_src/wagtailadmin/fonts/
* Click 'Selection', then:
* From the hamburger menu next to Font Awesome, 'Remove Set'
* from the hamburger menu next to Wagtail, 'Deselect' then 'Download JSON'; save it to wagtail/admin/static_src/wagtailadmin/fonts/wagtail-icomoon.json
* Reopen wagtail/admin/static_src/wagtailadmin/fonts/wagtail-icomoon.json from 'import project' and confirm that the icons are still there...
* Update wagtail/admin/static_src/wagtailadmin/scss/_variables-icons.scss with entries for your new icons, using the hex code you noted down.
* Update wagtail/contrib/styleguide/templates/wagtailstyleguide/base.html and add the icon to the 'icons' section.
