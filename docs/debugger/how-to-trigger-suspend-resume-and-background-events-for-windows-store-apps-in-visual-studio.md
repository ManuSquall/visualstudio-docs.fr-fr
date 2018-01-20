---
title: "Comment déclencher suspendre, reprendre et événements en arrière-plan pendant le débogage d’applications UWP | Documents Microsoft"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 036362ec392e6deba9bed1ef185c602d508d4da4
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Comment déclencher suspendre, reprendre et événements en arrière-plan pendant le débogage d’applications UWP dans Visual Studio
Lorsque vous n'effectuez pas de débogage, Windows **Process Lifetime Management** (PLM) contrôle l'état d'exécution de votre application, soit son démarrage, sa suspension, sa reprise et sa fin en réponse aux actions utilisateur et à l'état du périphérique. Lorsque vous effectuez un débogage, Windows désactive ces événements d'activation. Cette rubrique décrit comment déclencher ces événements dans le débogueur.  
  
 Cette rubrique décrit également comment déboguer les **tâches en arrière-plan**. Les tâches en arrière-plan vous permettent d'effectuer certaines opérations dans un processus en arrière-plan, même lorsque votre application n'est pas en cours d'exécution. Utilisez le débogueur pour placer votre application en mode débogage, puis, sans démarrer l'interface utilisateur, démarrez et déboguez la tâche en arrière-plan.  
  
 Pour plus d’informations sur les tâches de gestion de durée de vie des processus et d’arrière-plan, consultez [lancement, la reprise et les travaux multitâches](/windows/uwp/launch-resume/index).  
  
##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Déclencher les événements PLM (Process Lifetime Management)  
 Windows peut suspendre votre application lorsque l'utilisateur la quitte ou lorsque Windows entre dans un état de faible consommation d'énergie. Répondez à l'événement `Suspending` pour enregistrer des données appropriées relatives à l'application et aux utilisateurs dans un espace de stockage permanent et pour libérer les ressources. Lorsqu'une application quitte l'état **Suspendu** , elle entre dans l'état **Exécution** et reprend là où elle a été suspendue. Vous pouvez répondre à l'événement `Resuming` pour restaurer ou actualiser l'état de l'application et pour libérer les ressources.  
  
 Même si Windows essaie de conserver en mémoire autant d'applications suspendues que possible, Windows peut arrêter votre application si les ressources sont insuffisantes pour les conserver en mémoire. Un utilisateur peut également explicitement fermer votre application. Il n'existe aucun événement spécial qui indique que l'utilisateur a fermé une application.  
  
 Dans le débogueur Visual Studio, vous pouvez suspendre, reprendre et arrêter manuellement vos applications pour déboguer des événements du processus de cycle de vie. Pour déboguer un événement de processus du cycle de vie :  
  
1.  Définissez un point d'arrêt dans le gestionnaire de l'événement que vous souhaitez déboguer.  
  
2.  Appuyez sur **F5** pour démarrer le débogage.  
  
3.  Dans la barre d'outils **Emplacement de débogage** , choisissez l'événement à déclencher :  
  
     ![Suspendre, reprendre, terminer et tâches en arrière-plan](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
     Notez que **Interrompre et quitter** ferme l'application et termine la session de débogage.  
  
##  <a name="BKMK_Trigger_background_tasks"></a> Déclencher les tâches en arrière-plan  
 Une application peut enregistrer une tâche en arrière-plan pour répondre à certains événements système, même si l'application n'est pas en cours d'exécution. Les tâches en arrière-plan ne peuvent pas exécuter le code qui met à jour directement l'interface utilisateur; En fait, elles affichent des informations à l'utilisateur avec des mises à jour de mosaïque, des mises à jour de badge et des notifications contextuelles. Pour plus d'informations, consultez [Supporting your app with background tasks](http://msdn.microsoft.com/en-us/4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
 Déclenchez les événements qui démarrent les tâches en arrière-plan pour votre application à partir du débogueur.  
  
> [!NOTE]
>  Le débogueur peut déclencher uniquement les événements qui ne contiennent pas de données, comme les événements qui indiquent un changement d'état sur le périphérique. Vous devez déclencher manuellement les tâches en arrière-plan qui nécessitent la saisie utilisateur ou d'autres données.  
  
 La méthode la plus réaliste pour déclencher un événement de tâche en arrière-plan est le moment où votre application n'est pas en cours d'exécution. Toutefois, le déclenchement de l'événement dans une session de débogage standard est également pris en charge.  
  
###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Déclencher un événement de tâche en arrière-plan à partir d'une session de débogage standard  
  
1.  Définissez un point d'arrêt dans le code d'une tâche en arrière-plan à déboguer.  
  
2.  Appuyez sur **F5** pour démarrer le débogage.  
  
3.  Dans la liste des événements dans la barre d'outils **Emplacement de débogage** , choisissez la tâche en arrière-plan à démarrer.  
  
     ![Suspendre, reprendre, terminer et tâches en arrière-plan](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Déclencher une tâche en arrière-plan lorsque l'application n'est pas en cours d'exécution  
  
1.  Définissez un point d'arrêt dans le code d'une tâche en arrière-plan à déboguer.  
  
2.  Ouvrez la page des propriétés de débogage du projet de démarrage. Dans l'Explorateur de solutions, sélectionnez le projet. Dans le menu **Déboguer** , choisissez **Propriétés**.  
  
     Pour les projets C++ et JavaScript, développez **propriétés de Configuration** , puis **débogage**.  
  
3.  Effectuez l’une des opérations suivantes :  
  
    -   Pour les projets Visual C# et Visual Basic, choisissez **Ne pas lancer, mais déboguer mon code au démarrage**  
  
         ![C &#35; &#47; Propriété d’application VB débogage lancement](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")  
  
    -   Pour les projets JavaScript et Visual C++, choisissez **Non** dans la liste **Lancer l'application** .  
  
         ![C &#43; &#43; &#47; Propriété de débogage d’application VB lancer](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")  
  
4.  Appuyez sur **F5** pour exécuter l'application en mode débogage. Notez que la liste **Processus** dans la barre d'outils **Emplacement de débogage** affiche le nom du package d'application pour indiquer que vous êtes en mode débogage.  
  
     ![Liste des processus en arrière-plan tâches](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")  
  
5.  Dans la liste des événements dans la barre d'outils **Emplacement de débogage** , choisissez la tâche en arrière-plan à démarrer.  
  
     ![Suspendre, reprendre, terminer et tâches en arrière-plan](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Déclencher les événements PLM (Process Lifecycle Management) et les tâches en arrière-plan depuis une application installée  
 Utilisez le **déboguer le Package d’application installé** boîte de dialogue pour charger une application déjà installée dans le débogueur. Par exemple, vous pourrez déboguer une application qui a été installée à partir de Microsoft Store ou déboguer une application lorsque vous avez les fichiers sources pour l’application, mais pas un projet Visual Studio pour l’application. Le **déboguer le Package d’application installé** boîte de dialogue vous permet de démarrer une application en mode débogage sur l’ordinateur Visual Studio ou sur un périphérique distant, ou pour configurer l’application pour s’exécuter en mode débogage sans la démarrer. Pour plus d’informations, consultez [déboguer un package d’application installés](../debugger/debug-installed-app-package.md).
  
 Une fois l'application chargée dans le débogueur, vous pouvez utiliser l'une des procédures décrites ci-dessus.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostic des erreurs d'activation des tâches en arrière-plan  
 Les journaux de diagnostic dans l’Observateur d’événements Windows pour infrastructure en arrière-plan contient des informations détaillées que vous pouvez utiliser pour diagnostiquer et résoudre les erreurs des tâches en arrière-plan. Pour consulter le journal :  
  
1.  Ouvrez l'application Observateur d'événements.  
  
2.  Dans le volet **Actions** , choisissez **Afficher** et assurez-vous que la case à cocher **Afficher les journaux d’analyse et de débogage** est activée.  
  
3.  Sur le **l’Observateur d’événements (Local)** d’arborescence, développez les nœuds **journaux des Applications et Services** > **Microsoft** > **Windows**   >  **BackgroundTasksInfrastructure**.  
  
4.  Choisissez le journal **Diagnostic** .  
  
## <a name="see-also"></a>Voir aussi  
 [Test d’applications UWP avec Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Cycle de vie des applications](/windows/uwp/launch-resume/app-lifecycle)   
 [Lancement de la reprise et multitâche](/windows/uwp/launch-resume/index)