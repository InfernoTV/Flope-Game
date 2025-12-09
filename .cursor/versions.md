# Version History

## Version 0.02 - UI Customization and Credits Redirect
**Date**: 2024

### Changes
- **Added**: Credits button interception system - redirects to random URL (50% guns.lol/infernoytv, 50% feds.lol/infernoytv) in new tab
- **Added**: Multiple interception methods for Unity credits button (window.open override, postMessage listener, SendMessage override)
- **Renamed**: "Slope" to "Flope" throughout documentation and text files
- **Updated**: Product name in Build/slope.json from "Slope" to "Flope"
- **Updated**: All text references in README.md and scope.md
- **Note**: Unity build file names (slope.json, slope_*.unityweb) kept unchanged for compatibility
- **Note**: Green colors in game UI are in compiled Unity assets and cannot be modified without Unity source project

### Technical Details
- Implemented comprehensive Unity message interception system
- Overrides window.open to catch credits navigation
- Listens for postMessage events from Unity
- Provides global OpenCredits() function for Unity to call
- Attempts to override Unity's SendMessage function

### Limitations
- Buttons, leaderboard, and login UI elements are rendered inside Unity canvas and cannot be removed without Unity source
- Green colors in game UI are compiled into Unity build files and require Unity editor to modify
- File names (slope.json, etc.) must remain for Unity build compatibility

## Version 0.01 - Initial Cleanup and Documentation
**Date**: 2024

### Changes
- **Removed**: All Google AdSense scripts and ad-related code
- **Removed**: Google Analytics (gtag.js) tracking
- **Removed**: Clicky analytics tracking
- **Removed**: ads.txt file
- **Updated**: Alert banner message to remove ad-related text
- **Added**: Comprehensive game scope description in scope.md
- **Added**: Version tracking system (APP_VERSION constant)
- **Added**: Version history documentation

### Technical Details
- Cleaned index.html of all advertising and analytics scripts
- Maintained core game functionality (Unity WebGL loader and game container)
- Preserved all game assets and build files
- No breaking changes to game functionality
