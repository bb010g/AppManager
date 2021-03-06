---
next: false
sidebarDepth: 2
---
# Miscellanea

::: details Table of Contents
[[toc]]
:::

## I don't use root/ADB. Am I completely safe from any harms?
Yes. AM cannot modify any system settings without root or ADB over TCP.

## Why does AM have the INTERNET permission when it doesn't connect to the Internet?
AM uses the INTERNET permission for the following reasons:
1. **To provide ADB over TCP support for the non-root users.** ADB over TCP is a custom network protocol that usually runs on port `5555`. Therefore, to connect to this port via localhost, AM needs this permission.
2. **To execute privileged code both on root and ADB mode.** AM, being a user app, cannot execute privileged code nor can it access any hidden APIs. Consequently, AM runs a server in the privileged environment using `app_process` at port `60001` and on the user side, AM connects to this server and execute privileged code remotely from the app. Now, there are alternative ways to communicate with a remote service. Currently they are under consideration.

## How are trackers and libraries are updated?
Trackers and libraries are updated manually before making a new release.

## Any plans for Shizuku?
App Manager's use of hidden API and privileged code execution is now much more complex and cannot be integrated with other third party apps such as [Shizuku][shizuku]. Here are some reasons for not considering Shizuku (which now has Apache 2.0 license) for App Manager:
1. Shizuku was initially non-free which led me to use a similar approach for App Manager to support both root and ADB
1. App Manager already supports both ADB and root which in some cases is more capable than Shizuku
2. Relying on a third-party app for the major functionalities is not a good design choice
3. Integration of Shizuku will increase the complexity of App Manager.

## What are bloatware and how to remove them?
Bloatware are the unnecessary apps supplied by the vendor or OEM and are usually system apps. These apps are often used to track users and collect user data which they might sell for profits. System apps do not need to request any permission in order to access device info, contacts and messaging data, and other usage info such as your phone usage habits and everything you store on your shared storage(s).

The bloatware may also include Google apps (such as Google Play Services, Google Play Store, Gmail, Google, Messages, Dialer, Contacts), Facebook apps (the Facebook app consists of four or five apps), Facebook Messenger, Instagram, Twitter and many other apps which can also track users and/or collect user data without consent given that they all are system apps. You can disable a few permissions from the Android settings but be aware that Android settings hides almost every permission any security specialist would call potentially _dangerous_.

If the bloatware were user apps, you could easily uninstall them either from Android settings or AM. Uninstalling system apps is not possible without root permission. You can also uninstall system apps using ADB, but it may not work for all apps. AM can uninstall system apps with root or ADB (the latter with certain limitations, of course), but these methods cannot _remove_ the system apps completely as they are located in the _system_ partition which is a read-only partition. If you have root, you can remount this partition to manually _purge_ these apps but this will break Over the Air (OTA) updates since data in the system partition has been modified. There are two kind of updates, delta (small-size, consisting of only the changes between two versions) and full updates. You can still apply full updates, but the bloatware will be installed again, and consequently, you have to delete them all over again. Besides, not all vendors provide full updates.

Another solution is to disable these apps either from Android settings (no-root) or AM, but certain services can still run in the background as they can be started by other system apps using Inter-process Communication (IPC). One possible solution is to disable all bloatware until the service has finally stopped (after a restart). However, due to heavy modifications of the Android frameworks by the vendors, removing or disabling certain bloatware may cause the System UI to crash or even cause bootloop, thus, (soft) bricking your device. You may search the web or consult the fellow users to find out more about how to debloat your device.

From v2.5.19, AM has a new feature called [profiles][profile]. The [profiles page][profiles] has an option to create new profiles from one of the presets. The presets consist of debloating profiles which can be used as a starting point to monitor, disable, and remove the bloatware from a proprietary Android operating system.

::: tip Note
In most cases, you cannot completely debloat your device. Therefore, it is recommended that you use a custom ROM free of bloatware such as Graphene OS, Lineage OS or their derivatives.
:::

[shizuku]: https://shizuku.rikka.app
[profile]: ../guide/profile-page.md
[profiles]: ../guide/profiles-page.md
