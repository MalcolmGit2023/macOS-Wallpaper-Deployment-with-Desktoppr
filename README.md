
# macOS Wallpaper Deployment with Desktoppr — Summary

This repository documents the workflow used to deploy custom wallpapers to macOS using the **desktoppr** CLI and Jamf Pro, bundled via the **Packages** app so all components install together.

View Wiki page - https://github.com/MalcolmGit2023/macOS-Wallpaper-Deployment-with-Desktoppr/wiki

## What I did

1. **Downloaded desktoppr**
   - Binary from: https://github.com/scriptingosx/desktoppr

2. **Wrote and tested a Bash script** to set the wallpaper
   - Detects the logged-in user
   - Determines display resolution (width)
   - Selects an appropriate wallpaper
   - Applies it using `desktoppr`
   - Logs to `/var/log/wallpaper_change.log`

3. **Selected wallpapers**
   - Used 3 images (works fine with 1 or 2 as well)

4. **Built a single package with the Packages app (on MacBook)**
   - Included:
     - `desktoppr` command-line binary
     - The chosen wallpapers
     - A **post-install script** runs the desktoppr command line.

5. **Deployed via Jamf Pro**
   - Uploaded the package and scoped to target Macs

## Paths used in the package
- `desktoppr` installed to: `/usr/local/bin/desktoppr`
- wallpapers to: `/Library/Application Support/wallpapers/`
- script to: `/Library/Application Support/wallpapers/scripts/set_wallpaper.sh`

## Notes
- Log file: `/var/log/wallpaper_change.log`
- Adjust resolution thresholds or filenames in `scripts/set_wallpaper.sh` as needed.
- Original desktoppr project: https://github.com/scriptingosx/desktoppr
