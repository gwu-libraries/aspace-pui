# GW Libraries ArchivesSpace Public User Interface

The GW Libraries ArchivesSpace PUI customization files and documentation can be found in this repo.

## Version
These configurations have been tested with ArchivesSpace [version 2.3.2](https://github.com/archivesspace/archivesspace/releases/tag/v2.3.2) and [version 2.5.2](https://github.com/archivesspace/archivesspace/releases/tag/v2.5.2).


# Edits were made in two areas for the PUI:
1. Configurations to the core code configuration file config.rb, found at /path/to/aspace/config/config.rb. These configurations are described below.
2. Customizations to the built-in "local" plugin, specifically its "public" directory, found at /path/to/aspace/plugins/local/public/. These customized files are located in this repo's/public/ directory, and are also described below.

## 1. Config.rb
1. Logo: uploaded image file to the "public" plugin (see the file in this repo) and updated the path in config.rb
```
AppConfig[:pui_branding_img] = '/assets/images/gw_iddol_lib_2cs_rev-01.png.png'
```

2. Updated tabs that appear in the main menu. Initially, all lines are commented out and marked as false. The uncommented lines that equal true are edits.
```
## The following determine which 'tabs' are on the main horizontal menu
#AppConfig[:pui_hide] = {}
AppConfig[:pui_hide][:repositories] = true
#AppConfig[:pui_hide][:resources] = false
AppConfig[:pui_hide][:digital_objects] = true
AppConfig[:pui_hide][:accessions] = true
#AppConfig[:pui_hide][:subjects] = false
#AppConfig[:pui_hide][:agents] = false
AppConfig[:pui_hide][:classifications] = true
#AppConfig[:pui_hide][:search_tab] = false
```

3. The citation button and request button were removed by uncommenting two lines below and changing to "false".
```
## Enable / disable PUI resource/archival object page actions
AppConfig[:pui_page_actions_cite] = false
#AppConfig[:pui_page_actions_bookmark] = true
AppConfig[:pui_page_actions_request] = false
#AppConfig[:pui_page_actions_print] = true
```

## 2. Local plugin
GW uses the built-in "local" plugin to customize the public portal of ArchivesSpace. All of the files that we added to this plugin are in this repo, and described below.
* assets/custom.css - custom CSS file, which overwrites the default styling. Explanations for each overwrite are in the custom.css file itself.
* assets/fonts/[fontfile.otf] - font file used by GW is excluded from this repo due to copyright, but would be located here
* assets/images/gw_iddol_lib_2cs_rev-01.png.png - logo image file, to replace the default ArchivesSpace logo. Dropping the logo here doesn't automatically replace the default logo; it has to be updated in the config.rb file as well (see above).
* assets/js/gw-scripts.js - javascript fiel that adds a message to certain pages (based on URL) with instructions for requesting boxes. linked from views/layouts/application.html.erb
* locales/en.yml - Ruby on Rails vocabulary file, where we set the header title, welcome text on home page, and other standard vocabulary terms throughout the site. Having this file in the plugin overwrites the equivalent file in the core code. 
* views/shared/_footer.html.erb - customized footer, which is based on and overwrites the equivalent file in the core code. 
* views/shared/_header.html.erb - customized header, which is based on and overwrites the equivalent file in the core code. 
* views/layouts/application.html.erb - customized shared layout file for all pages. link to javascript file (js/gw-scripts.js) was added to this file, for the purpose of adding a message to certain pages (based on URL) with instructions for requesting boxes 
* views/layout_head.html.erb - this file is used to "activate" the custom css file
