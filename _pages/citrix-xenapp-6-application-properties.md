---
title: Citrix XenApp 6 Application Properties
permalink: /citrix-xenapp-6-application-properties
layout: page
comments: false
---

| Property type | Property name | Description |
| ------ |--- | --- |
| ApplicationType  | ApplicationType | The type of application |
| String | DisplayName | The name of the application. This name is not guaranteed to be unique in the system, however the name must be unique under the parent folder where the application is located. The length of the name may not exceed 255 characters. |
| String | Description | Description for the published application. The length of the description may not exceed 255 characters |
| String | FolderPath | The parent folder path of the published application |
| String | BrowserName | Published application's name. Must be unique in a farm. Cannot be null. The length of the name may not exceed 48 characters. The name may not contain these characters: %/\$# |
| Boolean | Enabled | If true, the published object will be available to users |
| Boolean | HideWhenDisabled | If set to true, hide the application when disabled |
| String | ContentAddress | UNC or URL of the published content |
| String | CommandLineExecutable | The default initial program |
| String | WorkingDirectory | The default working directory (overridable on a per-server basis), or empty for a server desktop or not to specify a working directory |
| String | ProfileLocation | The UNC path of the profile to use by default |
| String | ProfileProgramName | The name of the application in the profile to use |
| String | ProfileProgramArguments | The arguments to pass into the streamed application |
| Boolean | AnonymousConnectionsAllowed | If value is true, it allow all client users to start the application without specifying a user name, domain name and password |
| String | ClientFolder | The location of the app in the Program Neighborhood interface, backslash-delimited. |
| Boolean | AddToClientStartMenu | If set to true, create a shortcut in the client’s start menu |
| String | StartMenuFolder | The location of the shortcut within the start menu, backslash-delimited. This property is valid only when AddToClientStartMenu is true |
| Boolean | AddToClientDesktop | If set to true, create a shortcut to this application on the user’s local desktop |
| Boolean | ConnectionsThroughAccessGatewayAllowed | If set to true, allow connections to this application through Citrix Access Gateway |
| Boolean | OtherConnectionsAllowed | If set to true, allow connections to this application through things other than Citrix Access Gateway |
| Boolean | AccessSessionConditionsEnabled | Whether the list of conditions is enabled |
| String[] | AccessSessionConditions | A collection of access conditions, at least one of which must be met by incoming Access Gateway connections. This collection might be empty but it won't be null. This collection is ignored if AllowConnectionsThroughAccessGateway is false. If this collection is empty, then any Citrix Access Gateway connection is allowed. Otherwise, the Citrix Access Gateway connection must meet at least one filter-farm combination in this list. The first part of the KeyValuePair is the Access Gateway farm name and the second part of the pair is the filter name |
| Int32 | InstanceLimit | Restrict the number of concurrent instances of this published application in the farm to this number. Specify -1 for no limit. Zero is not a legal value for this property |
| Boolean | MultipleInstancesPerUserAllowed | If set to true, limit each user to only one instance of this application at a time |
| CpuPriorityLevel  | CpuPriorityLevel | The CPU priority level to use for this application. By default, this is CpuPriorityLevel.Normal |
| AudioType  | AudioType | The legacy audio type to use by default |
| Boolean | AudioRequired | If set to true, deny connections that cannot support the default audio type. This property is valid only if DefaultAudioType is not NotRequired. |
| Boolean | SslConnectionEnabled | If set to true, allow SSL connections to this application. Note that this cannot be enforced as a minimum requirement on the client side |
| EncryptionLevel  | EncryptionLevel | The default encryption level for the application's sessions |
| Boolean | EncryptionRequired | If set to true, deny connections that cannot support the default encryption level. This property is valid only if DefaultEncryptionLevel is not Basic |
| Boolean | WaitOnPrinterCreation | If set to true, wait for printers to be auto-created before starting this application |
| String | WindowType | The window size/type to use by default |
| ColorDepth  | ColorDepth | The color depth to use by default |
| Boolean | TitleBarHidden | If set to true, hide the application window's title bar |
| Boolean | MaximizedOnStartup | If set to true, maximize the application window on startup |
| Boolean | OfflineAccessAllowed | If set to true, support offline access |
| StreamedAppCaching Option  | CachingOption | The type of caching to use for this streamed application. This property is valid only if AllowOfflineAccess is set to true |
| AlternateProfile[]  | AlternateProfiles | A collection of alternate UNC paths and IP addresses to use for this streamed application, to provide better performance |
| Boolean | RunAsLeastPrivilegedUser | If set to true, run this streamed application as a least-privileged user |