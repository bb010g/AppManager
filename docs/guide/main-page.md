---
next: ./app-details-page
prev: ./adb-over-tcp
sidebarDepth: 2
---
# Main Page

Main page lists all the installed apps (or a list of apps supplied by any third-party application) as well as apps that has existing backups. A single click on any installed app item opens the respective [App Details][4] page. Using the [sort](#sort) option from the menu, the app items can be sorted in various ways and preserved on close. It also possible to filter items based on your needs using the [filter](#filter) option in the menu. You can filter using more than one options. You can also filter apps using app labels or package name using the search button.

::: details Table of Contents
[[toc]]
:::

## Batch Operations
Batch operations or operation on multiple apps are also available within this page (most these operations require root or [ADB over TCP][1]). To enable multiple selection mode, click on any app icon or long click on any app. After that you can use the regular click to select apps instead of opening the [App Details][4] page. These operations include:
- Backup APK file (no root)
- [Backup/restore/delete app data][backup_restore]
- Clear data from apps
- Enable/disable/force-stop/uninstall apps
- Disable run in background
- Block ad and tracker components
- Export blocking rules
- Add the selected apps to a [profile][profiles]

## Colour Codes
Here's a list of colours used in this page and their meaning:
- <code style="background-color: #FCEED1; color: #000">Light greyish orange (day)</code> / <code style="background-color: #091F36; color: #FFF">dark blue (night)</code> - App selected for batch operation
- <code style="background-color: #FF8A80; color: #000">Light red (day)</code> / <code style="background-color: #4F1C14; color: #FFF">very dark red (night)</code> - Disabled app
- <code style="background-color: yellow; color: #000">Yellow Star</code> - App is in debug mode
- <code style="color: #E05915">Orange _Date_</code> - App can read logs (permission granted)
- <code style="color: #E05915FF">Orange _UID_</code> - User ID is being shared between apps
- <code style="color: #E05915FF">Orange _SDK/Size_</code> - Uses cleartext (ie. HTTP) traffic
- <code style="color: red">Red _package name_</code> - App does not allow clearing data
- <code style="color: red">Red _backup_</code> - App not installed but has one or more backups
- <code style="color: #09868BFF">Dark cyan _Package name_</code> - Stopped or forced closed app
- <code style="color: #09868BFF">Dark cyan _Version_</code> - Inactive app
- <code style="color: magenta">Magenta</code> - Persistent app ie., remains running all the time

## Application Types
An app is either **User App** or **System App** along with the following codes:
- `X` - The app supports multiple architectures: 32-bit, 64-bit or arm-v7, arm-v8, etc.
- `0` - App does not have code with it
- `°` - App is in suspended state
- `#` - App has requested a large heap
- `?` - App has requested VM in safe mode

## Version Info
Version name is followed by the following prefixes:
- `_` - No hardware acceleration
- `~` - Test only mode
- `debug` - Debuggable app

## Options Menu
Options menu has several options which can be used to sort, filter the listed apps as well as navigate to different pages.

### Instructions
Clicking on instructions open an offline version of the App Manager documentations. It opens the online version if the corresponding feature split ie. <tt>feat_docs</tt> is not installed.

### List Options
List options contain the options to sort or filter the app list.

#### Sort
Apps listed on the main page can be sorted in different ways. The sorting preference is preserved which means the apps will be sorted the same way that was sorted in the previous launch. Regardless of your sorting preference, however, the apps are first sorted alphabetically to prevent random results.
- **User app first.** User apps are listed on top
- **App label.** Sort in ascending order based on the app labels (also known as _app names_). This is the default sorting preference
- **Package name.** Sort in ascending order based on package names
- **Last update.** Sort in descending order based on the package update date (or install date if it is a newly installed package)
- **Shared user ID.** Sort in descending order based on the kernel user ID
- **Target SDK.** Sort in ascending order based on the target SDK
- **Signature.** Sort in ascending order based on app's signing info
- **Disabled first.** List disabled apps first
- **Blocked first.** Sort in descending order based on the number of blocked components
- **Backup first.** Display apps with backups on top

There is also a _reverse_ option which can be used to sort the apps in reverse order.

#### Filter
Apps listed on the main page can be filtered in a number of ways. Like sorting, filtering preferences are also stored and retained after a relaunch.
- **User apps.** List only the user apps
- **System apps.** List only the system apps
- **Disabled apps.** List only the disabled apps
- **Apps with rules.** List the apps with one or more blocking rules
- **Apps with activities.** List the apps with one or more activities
- **Apps with backups.** List apps with one or more backups (including uninstalled apps)
- **Running apps.** List apps that are currently running (either in foreground or background)
- **Apps with splits.** List apps with one or more split APKs
- **Installed apps.** List only installed apps

Unlike sorting, you can filter using more than one option. For example, you can list the disabled user apps by filtering app lists selecting _user apps_ and _disabled apps_. This is particularly useful for [batch operations](#batch-operations) where you can filter all user apps to carry out certain operations.

### 1-Click Ops
**1-Click Ops** stands for **One-Click Operations**. You can directly open the corresponding page by clicking on this option.

_See also: [1-Click Ops Page][5]_

### App Usage
App usage statistics such as _screen time_, _data usage_ (both mobile and Wifi), _number of times an app was opened_ can be accessed by clicking on the **App Usage** option in the menu (requires _Usage Access_ permission).

### System Config
Display various system configurations, whitelists/blacklists included in Android by either OEM/vendor, AOSP or even some Magisk modules.

### Running Apps
A list of running apps or processes can be viewed by clicking on the **Running Apps** option in the menu (requires root or [ADB][1]). Running apps or processes can also be force-closed or killed within the resultant page.

### APK Updater
If you have the app [APK Updater][3] installed, you can use the corresponding option in the menu to open the app directly. The option is hidden if you do not have it installed.

### Profiles
Opens the [profiles page][profiles]. Profiles are a way to configure regularly used tasks. You can also add shortcuts of the profiles in the launcher to run them directly.

### Termux
If you have [Termux][2] installed, you can directly go to the running session or open a new session using the **Termux** option in the menu.

### Settings
You can go to in-app [Settings][settings] by clicking on the corresponding option.

[1]: ./adb-over-tcp.md
[2]: https://github.com/termux/termux-app
[3]: https://github.com/rumboalla/apkupdater
[4]: ./app-details-page.md
[5]: ./one-click-ops-page.md
[settings]: ./settings-page.md
[profiles]: ./profiles-page.md
[backup_restore]: ./backup-restore.md
