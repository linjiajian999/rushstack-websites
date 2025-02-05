---
title: rush-plugin-manifest.json (experimental)
---

This is the template for the **rush-plugin-manifest.json** file that is used when
[creating a Rush plugin](../extensibility/creating_plugins).

**&lt;your plugin project&gt;/rush-plugin-manifest.json**

```js
/**
 * This file defines the Rush plugins that are provided by this package.
 */
{
  "$schema": "https://developer.microsoft.com/json-schemas/rush/v5/rush-plugin-manifest.schema.json",

  /**
   * An array of one or more plugin definitions provided by this NPM package.
   *
   * For more granular installations, it is recommended for plugins to be implemented by an
   * NPM package that does try to serve other roles such as providing APIs or command-line binaries.
   * The package name should start with "rush-".  The name should end with "-plugin" or "-plugins".
   * For example: "@scope/rush-business-policy-plugin"
   */
  "plugins": [
    {
      /**
       * (Required) The name of the plugin.  The plugin name must be comprised of letters and numbers
       * forming one or more words that are separated by hyphens.  Note that if the plugin has a
       * JSON config file, that filename will be the same as the plugin name.  See "optionsSchema" below
       * for details.
       *
       * If the manifest defines exactly one plugin, then it is suggested to reuse the name from the
       * NPM package.  For example, if the NPM package is "@scope/rush-business-policy-plugin"
       * then the plugin name might be "business-policy" and with config file "business-policy.json".
       */
      "pluginName": "example",

      /**
       * (Required) Provide some documentation that summarizes the problem solved by this plugin,
       * how to invoke it, and what operations it performs.
       */
      "description": "An example plugin",

      /**
       * (Optional) A path to a JavaScript code module that implements the "IRushPlugin" interface.
       * This module can use the "@rushstack/rush-sdk" API to register handlers for Rush events
       * and services.  The module path is relative to the folder containing the "package.json" file.
       */
      // "entryPoint": "lib/example/RushExamplePlugin.js",

      /**
       * (Optional) A path to a "command-line.json" file that defines Rush command line actions
       * and parameters contributed by this plugin.  This config file has the same JSON schema
       * as Rush's "common/config/rush/command-line.json" file.
       */
      // "commandLineJsonFilePath": "lib/example/command-line.json",

      /**
       * (Optional) A path to a JSON schema for validating the config file that end users can
       * create to customize this plugin's behavior.  Plugin config files are stored in the folder
       * "common/config/rush-plugins/" with a filename corresponding to the "pluginName" field
       * from the manifest.  For example: "common/config/rush-plugins/business-policy.json"
       * whose schema is "business-policy.schema.json".
       */
      // "optionsSchema": "lib/example/example.schema.json",

      /**
       * (Optional) A list of associated Rush command names such as "build" from "rush build".
       * If specified, then the plugin's "entryPoint" code module be loaded only if
       * one of the specified commands is invoked.  This improves performance by avoiding
       * loading the code module when it is not needed.  If "associatedCommands" is
       * not specified, then the code module will always be loaded.
       */
      // "associatedCommands": [ "build" ]
    }
  ]
}
```

## See also

- [Creating a Rush plugin](../extensibility/creating_plugins)
- [Using Rush plugins](../maintainer/using_rush_plugins)
