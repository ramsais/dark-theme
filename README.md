# SRS Dark Theme Plugin for JetBrains IDEs

A custom dark theme designed to reduce eye strain and provide a comfortable coding experience for JetBrains IDEs.

## Prerequisites

- Java Development Kit (JDK) 17 or later
- Gradle 8.x
- IntelliJ IDEA (for development)

## Compatibility

This plugin is compatible with IntelliJ-based IDEs version 2025.1 (build 251.*) and newer, up to version 2025.3 (build 253.*).

## Running and Testing the Plugin

### Building the Plugin

To build the plugin, run the following command from the project root:

```bash
./gradlew build
```

This will compile the code, run tests, and create a plugin distribution in the `build/distributions` directory.

### Running Tests

To run the tests for the plugin, use:

```bash
./gradlew test
```

This will execute all the tests in the project. The test results will be available in the `build/reports/tests` directory.

### Running the Plugin in a Development IDE

To run the plugin in a development instance of IntelliJ IDEA, use:

```bash
./gradlew runIde
```

This will start a new instance of IntelliJ IDEA with the plugin installed. You can then test the theme by:

1. Going to Settings/Preferences (Ctrl+Alt+S or ⌘,)
2. Navigate to Appearance & Behavior > Appearance
3. Select "SRS Dark Theme" from the Theme dropdown
4. Click Apply and OK

### Modifying Theme Styles on the Go

The plugin is configured for hot-reloading of theme resources, allowing you to modify theme files and see changes in real-time without rebuilding or reinstalling the plugin:

1. Run the plugin in development mode using the dedicated theme development task:
   ```bash
   ./gradlew watchTheme
   ```

   Or alternatively, use the standard run task:
   ```bash
   ./gradlew runIde
   ```

2. While the development IDE is running, make changes to theme files:
   - Edit `/src/main/resources/theme/srs-dark-theme.theme.json` for UI theme changes
   - Edit `/src/main/resources/theme/srs-dark-editor.xml` for editor color scheme changes

3. Save your changes. The theme will automatically reload in the development IDE.

4. If changes are not immediately visible, you can force a refresh by:
   - Switching to another theme and back to "SRS Dark Theme"
   - Or restarting the IDE with the "File > Invalidate Caches / Restart..." option

This hot-reload feature significantly speeds up theme development by providing immediate visual feedback for your changes.

### Creating a Plugin Distribution

To create a distributable plugin ZIP file, run:

```bash
./gradlew buildPlugin
```

The plugin ZIP file will be created in the `build/distributions` directory. You should see a file named `plugins-1.0.0.zip` (or similar, depending on the version number in your build.gradle file).

**Note:** The standard `./gradlew build` command will also create this ZIP file in the same location.

## Installing the Plugin in a JetBrains IDE

### From a ZIP File

1. Download the plugin ZIP file from the `build/distributions` directory
2. Open your JetBrains IDE
3. Go to Settings/Preferences (Ctrl+Alt+S or ⌘,)
4. Navigate to Plugins
5. Click the gear icon and select "Install Plugin from Disk..."
6. Select the ZIP file you downloaded
7. Restart the IDE when prompted

### From the JetBrains Marketplace

Once the plugin is published to the JetBrains Marketplace:

1. Open your JetBrains IDE
2. Go to Settings/Preferences (Ctrl+Alt+S or ⌘,)
3. Navigate to Plugins
4. Click on the "Marketplace" tab
5. Search for "SRS Dark Theme"
6. Click "Install"
7. Restart the IDE when prompted

## Publishing the Plugin

To publish the plugin to the JetBrains Marketplace, you need to:

1. Create a plugin distribution:
   ```bash
   ./gradlew buildPlugin
   ```

2. Upload the plugin to the JetBrains Marketplace:
   ```bash
   ./gradlew publishPlugin
   ```

   Note: You need to set the `intellijPublishToken` in your `gradle.properties` file or as an environment variable.

## Troubleshooting

If you encounter any issues:

- Make sure you're using JDK 17 or later
- Ensure Gradle is properly configured
- Check the build logs for any error messages
- Verify that the plugin.xml file is correctly formatted
- Make sure the theme files are in the correct location

### Compatibility Issues

If you see an error like "Plugin 'SRS Dark Theme' is not compatible with the current version of the IDE":

1. Check the compatibility section above to see which IDE versions are supported
2. If you need to use the plugin with a different IDE version, you can modify the `build.gradle` file:
   - Update the `intellij.version` property to match your IDE version
   - Update the `sinceBuild` and `untilBuild` properties in the `patchPluginXml` section
   - Rebuild the plugin using `./gradlew buildPlugin`

### Can't Find the ZIP File

If you've run `./gradlew build` or `./gradlew buildPlugin` but can't find the ZIP file:

1. Make sure the build completed successfully without errors
2. Check the exact path: `<project_root>/build/distributions/plugins-1.0.0.zip`
3. If the `build/distributions` directory doesn't exist, try running `./gradlew clean buildPlugin`
4. If you're using a file explorer, make sure hidden files and directories are visible (the `build` directory might be hidden)

## License

This project is licensed under the MIT License - see the LICENSE file for details.
