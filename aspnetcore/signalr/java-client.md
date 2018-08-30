---
title: ASP.NET Core SignalR Java client
author: mikaelm12
description: Learn how to use the ASP.NET Core SignalR Java client.
monikerRange: '>= aspnetcore-2.2'
ms.author: mimengis
ms.custom: mvc
ms.date: 08/30/2018
uid: signalr/java-client
---
# ASP.NET Core SignalR Java Client

By [Mikael Mengistu](https://twitter.com/MikaelM_12)

The Java client enables connecting to an ASP.NET Core SignalR server from Java code, including Android apps. Like the [JavaScript client](xref:signalr/javascript-client) and the [.NET client](xref:signalr/javascript-client), the Java client enables you to receive and send and receive messages to a hub in real time. The Java client is available in ASP.NET Core 2.2 or later.

The sample Java console app referenced in this article uses the Java client.

[View or download sample code](https://github.com/aspnet/Docs/tree/master/aspnetcore/signalr/java-client/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample))

## Install the SignalR Java client package

The *signalr-0.1.0-preview1-35029* JAR file allows clients to connect to SignalR hubs.

If using Gradle, add the following line to the `dependencies` section of your *build.gradle* file:

```gradle
implementation 'com.microsoft.aspnet:signalr:0.1.0-preview1-35029'
```

If using Maven, add the following lines inside the `<dependencies>` element of your *pom.xml* file:

[!code-xml[pom.xml dependency element](java-client/sample/pom.xml?name=snippet_dependencyElement)]

## Connect to a hub

To establish a connection, create a `HubConnectionBuilder` and call `build`. The hub URL and log level can be configured while building a connection. Configure any required options by inserting any of the `HubConnectionBuilder` methods into `build`. Start the connection with `start`.

[!code-java[Build hub connection](java-client/sample/src/main/java/Chat.java?range=17-20)]

## Call hub methods from client

A call to `send` invokes the hub. Pass the hub method name and any arguments defined in the hub method to `send`.

[!code-java[send method](java-client/sample/src/main/java/Chat.java?range=31)]

## Call client methods from hub

Use `hubConnection.on` to define methods on the client that the hub can call. Define the methods after building but before starting the connection.

[!code-java[Define client methods](java-client/sample/src/main/java/Chat.java?range=22-24)]

## Known limitations

This is an early preview release of the Java client. There are many features that aren't yet supported. The RTM release will address the following gaps:

* Only primitive types can be accepted as parameters and return types.
* The APIs are synchronous.
* Only the "Send" call type is supported at this time. "Invoke" and streaming of return values aren't supported.
* The client doesn't currently support the [Azure SignalR Service](/azure/azure-signalr/).
* Only the JSON protocol is supported.
* Only the WebSockets transport is supported.

## Additional resources

* <xref:signalr/hubs>
* <xref:signalr/javascript-client>
* <xref:signalr/publish-to-azure-web-app>