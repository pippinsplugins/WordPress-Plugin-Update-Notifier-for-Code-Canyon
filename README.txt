# WordPress plugin Update Notifier

This is a simple WordPress plugin update notifier that will provide your plugin Buyers with a notification every time you issue a plugin update.

It's a very simple script that requires and assumes you have an XML file in your own server. This XML file serves as an endpoint for the script to check what the latest version of the plugin is, and compares it with the current version of the plugin installed in the Client's server.

One of the script **requirements** is that the version number are **floats**. Versions like 1.0, 1.1, 2.3 are acceptable and required.

## Installation

Upload the **notifier.xml** file to your own server (the update notifier on the Client sites will check this file for the latest version)

Copy the **update-notifier.php** file to the root of the plugin.

Edit your plugin's main file and include the **update-notifier.php** file with the following code:

	require('update-notifier.php');
	
Edit the **update-notifier.php** file and make the appropriate changes to the following constants:

	define( 'NOTIFIER_PLUGIN_NAME', 'Your Plugin Name' ); // The plugin name
	define( 'NOTIFIER_PLUGIN_SHORT_NAME', 'ABC' ); // The plugin short name. Use this if your plugin has a long name and messes up the menu items. Otherwise remove it.
	define( 'NOTIFIER_PLUGIN_FOLDER_NAME', 'name-of-your-plugin-folder' ); // The plugin folder name
	define( 'NOTIFIER_PLUGIN_FILE_NAME', 'main-plugin-file.php' ); // The plugin's main file name
	define( 'NOTIFIER_XML_FILE', 'http://yoururl.com/updates/notifier.xml' ); // The remote notifier XML file containing the latest version of the plugin and changelog
	define( 'NOTIFIER_CACHE_INTERVAL', 21600 ); // The time interval for the remote XML cache in the database (21600 seconds = 6 hours)
	
Everything should be in place now. Every time you submit a plugin update you should edit the XML file in your server and change the following code to the latest version you've updated:

	<latest>1.0</latest>
	
This way, your Clients will see an update notification on the WordPress admin panel informing them that there's a new version available and they should update.

**NOTE:** when you submit plugin updates make sure to update the plugin Version number in the top of the main plugin file.
