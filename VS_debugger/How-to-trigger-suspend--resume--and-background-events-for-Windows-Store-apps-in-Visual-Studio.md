---
title: "How to trigger suspend, resume, and background events for Windows Store apps in Visual Studio"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - FSharp
  - VB
  - CSharp
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-ide-debug
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 17
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - tr-tr
---
# How to trigger suspend, resume, and background events for Windows Store apps in Visual Studio
When you are not debugging, Windows **Process Lifetime Management** (PLM) controls the execution state of your app—starting, suspending, resuming, and terminating the app in response to user actions and the state of the device. When you are debugging, Windows disables these activation events. This topic describes how to fire these events in the debugger.  
  
 This topic also describes how to debug **Background tasks**. Background tasks enable you to perform certain operations in a background process, even when you app is not running. You can use the debugger to put your app in debug mode and then— without starting the UI—start and debug the background task.  
  
 For more information about Process Lifetime Management and background tasks see [Launching, resuming, and multitasking](assetId:///04307b1b-05af-46a6-b639-3f35e297f71b).  
  
##  <a name="BKMK_In_this_topic"></a> In this topic  
 [Trigger Process Lifetime Management events](#BKMK_Trigger_Process_Lifecycle_Management_events)  
  
 [Trigger background tasks](#BKMK_Trigger_background_tasks)  
  
-   [Trigger a background task event from a standard debug session](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)  
  
-   [Trigger a background task when the app is not running](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)  
  
 [Trigger Process Lifetime Management events and background tasks from an installed app](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)  
  
 [Diagnosing background task activation errors](#BKMK_Diagnosing_background_task_activation_errors)  
  
##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Trigger Process Lifetime Management events  
 Windows can suspend your app when the user switches away from it or when Windows enters a low power state. You can respond to the `Suspending` event to save relevant app and user data to persistent storage and to release resources. When an app is resumed from the **Suspended** state, it enters the **Running** state and continues from where it was when it was suspended. You can respond to the `Resuming` event to restore or refresh application state and reclaim resources.  
  
 Although Windows attempts to keep as many suspended apps in memory as possible, Windows can terminate your app if there aren't enough resources to keep it in memory. A user can also explicitly close your app. There's no special event to indicate that the user has closed an app.  
  
 In the Visual Studio debugger, you can manually suspend, resume, and terminate your apps to debug process lifecycle events. To debug a process lifecycle event:  
  
1.  Set a breakpooint in the handler of the event that you want to debug.  
  
2.  Press **F5** to start debugging.  
  
3.  On the **Debug Location** toolbar, choose the event that you want to fire:  
  
     ![Suspend, resume, terminate, and background tasks](../VS_debugger/media/DBG_SuspendResumeBackground.png "DBG_SuspendResumeBackground")  
  
     Note that **Suspend and terminate** closes the app and ends the debug session.  
  
##  <a name="BKMK_Trigger_background_tasks"></a> Trigger background tasks  
 Any app can register a background task to respond to certain system events, even when the app is not running. Background tasks can't run code that directly updates the UI; instead, they show information to the user with tile updates, badge updates, and toast notifications. For more information, see [Supporting your app with background tasks](assetId:///4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
 You can trigger the events that start background tasks for your app from the debugger.  
  
> [!NOTE]
>  The debugger can trigger only those events that do not contain data, such as events that indicate a change of state in the device. You have to manually trigger background tasks that require user input or other data.  
  
 The most realistic way to trigger a background task event is when your app is not running. However, triggering the event in a standard debugging session is also supported.  
  
###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Trigger a background task event from a standard debug session  
  
1.  Set a breakpoint in the background task code that you want to debug.  
  
2.  Press **F5** to start debugging.  
  
3.  From the events list on the **Debug Location** toolbar, choose the background task that you want to start.  
  
     ![Suspend, resume, terminate, and background tasks](../VS_debugger/media/DBG_SuspendResumeBackground.png "DBG_SuspendResumeBackground")  
  
###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Trigger a background task when the app is not running  
  
1.  Set a breakpoint in the background task code that you want to debug.  
  
2.  Open the debug property page for the start-up project. In Solution Explorer, select the project. On the **Debug** menu, choose **Properties**.  
  
     For C++ projects, you might have to expand **Configuration Properties** and then choose **Debugging**.  
  
3.  Do one of the following:  
  
    -   For Visual C# and Visual Basic projects, choose **Do not launch, but debug my code when it starts**  
  
         ![C&#35;&#47;VB debug launch application property](../VS_debugger/media/DBG_CsVb_DontLaunchApp.png "DBG_CsVb_DontLaunchApp")  
  
    -   For JavaScript and Visual C++ projects, choose **No** from the **Launch application** list.  
  
         ![C&#43;&#43;&#47;VB Launch application debug property](../VS_debugger/media/DBG_CppJs_DontLaunchApp.png "DBG_CppJs_DontLaunchApp")  
  
4.  Press **F5** to put the app in debug mode. Note the **Process** list on the **Debug Location** toolbar displays the app package name to indicate that you are in debug mode.  
  
     ![Background task Process list](../VS_debugger/media/DBG_BackgroundTask_ProcessList.png "DBG_BackgroundTask_ProcessList")  
  
5.  From the events list on the **Debug Location** toolbar, choose the background task that you want to start.  
  
     ![Suspend, resume, terminate, and background tasks](../VS_debugger/media/DBG_SuspendResumeBackground.png "DBG_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Trigger Process Lifetime Management events and background tasks from an installed app  
 Use the Debug Installed App dialog box to load an app that is already installed into the debugger. For example, you might debug an app that was installed from the Windows store, or debug an app when you have the source files for the app, but not a Visual Studio project for the app. The Debug Installed App dialog box allows you start an app in debug mode on the Visual Studio machine or on a remote device, or to set the app to run in debug mode but not start it. See the **Start an installed app in the debugger** section of either the [JavaScript](../VS_debugger/Start-a-debugging-session-for-Store-Apps-in-Visual-Studio--JavaScript-.md#BKMK_Start_an_installed_app_in_the_debugger) or [Visual C++, Visual C#, and Visual Basic](../VS_debugger/Start-a-debugging-session-for-a-Store-app-in-Visual-Studio--VB--C#--C---and-XAML-.md#BKMK_Start_an_installed_app_in_the_debugger) versions of **How to start a debugging session** for more information.  
  
 Once the app is loaded into the debugger, you can use any of the procedures described above.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnosing background task activation errors  
 The diagnostic logs in Windows Event Viewer for the background infrastructure contained detailed information that you can use to diagnose and troubleshoot background task errors. To view the log:  
  
1.  Open the Event Viewer application.  
  
2.  In the **Actions** pane, choose **View** and make sure **Show Analytic and Debug Logs** is checked.  
  
3.  On the **Event Viewer (Local)** tree, expand the nodes **Applications and Services Logs** / **Microsoft** / **Windows** / **BackgroundTasksInfrastructure**.  
  
4.  Choose the **Diagnostic** log.  
  
## See Also  
 [Testing Store apps with Visual Studio](../VS_IDE/Testing-Store-apps-with-Visual-Studio.md)   
 [Debug apps in Visual Studio](../VS_debugger/Debug-Store-apps-in-Visual-Studio.md)   
 [Application lifecycle](assetId:///53cdc987-c547-49d1-a5a4-fd3f96b2259d)   
 [Launching, resuming, and multitasking](assetId:///04307b1b-05af-46a6-b639-3f35e297f71b)