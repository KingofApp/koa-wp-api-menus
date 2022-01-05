## Menu routes for WordPress JSON REST API

[WordPress](http://www.wordpress.org/) plugin that extends the JSON REST [WP API](https://github.com/WP-API/WP-API) with new routes pointing to WordPress registered menus. Read the [WP API documentation](http://wp-api.org/).

[![Download from WordPress.org](https://kingofapp.com/wp-content/uploads/2021/06/logo-king-of-app-300x148.png.webp)](https://s3.eu-central-1.amazonaws.com/kingofapp.com/embed+plugins/koa-wp-api-menus.zip)

#### New routes available:

- `/menus` list of every registered menu.
- `/menus/<id>` data for a specific menu.
- `/menu-locations` list of all registered theme locations.
- `/menu-locations/<location>` data for menu in specified menu in theme location. 

Currently, the `menu-locations/<location>` route for individual menus will return a tree with full menu hierarchy, with correct menu item order and listing children for each menu item. The `menus/<id>` route will output menu details and a flat array of menu items. Item order or if each item has a parent will be indicated in each item attributes, but this route won't output items as a tree.
 
You can alter the V1 data arrangement of each individual menu items and children using the filter hook `json_menus_format_menu_item`.

#### WP API V2

In V1 of the REST API the routes are located by default at `wp-json/menus/` etc.

In V2 the routes by default are at `wp-json/wp-api-menus/v2/` (e.g. `wp-json/wp-api-menus/v2/menus/`, etc.) since V2 encourages prefixing and version namespacing. 

You can alter the V2 data arrangement of the REST response using the filter hooks
1. `rest_menus_format_menus` to alter the list of menu items returned (e.g from `wp-json/wp-api-menus/v2/menus/`)
2. `rest_menus_format_menu` to alter a single menu returned (e.g `wp-json/wp-api-menus/v2/menus/<id>`)
3. `rest_menus_format_menu_item` to alter the menu items returned (e.g `wp-json/wp-api-menus/v2/menus/<id>` `items` property)
