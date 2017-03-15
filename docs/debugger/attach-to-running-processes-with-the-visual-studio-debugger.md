---
title: "Attacher aux processus en cours d&#39;ex&#233;cution avec le d&#233;bogueur Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "débogage distant, attachement aux programmes"
  - "processus, attacher à des processus en cours d’exécution"
  - "Boîte de dialogue Attacher au processus"
  - "débogage (Visual Studio), attachement à des processus"
  - "débogueur, processus"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Attacher aux processus en cours d&#39;ex&#233;cution avec le d&#233;bogueur Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Attachement du débogueur Visual Studio à un processus est souvent utile lorsque vous n’avez pas démarré une application à partir de Visual Studio, mais que vous souhaitez déboguer. Par exemple, vous pouvez attacher à un processus IIS ou un service Windows qui héberge une application .NET. Le processus d’à que vous attacher peut être local ou distant. Autre exemple, que si vous exécutez l’application sans le débogueur et une exception, vous pourrez ensuite attacher au processus de l’application pour commencer le débogage en cours d’exécution.

Pour certains types d’applications (telles que les applications du Windows Store), ne pas attacher directement à un nom de processus, mais utiliser le **Déboguer le Package d’application installé** plutôt l’option de menu (voir tableau).

Pour vous aider à déterminer si vous devez attacher à un processus pour votre scénario, quelques exemples de scénarios de débogage les plus courants sont présentés ici. Lorsque plusieurs instructions sont disponibles, nous fournissons des liens.

|Scénario|Déboguer (méthode)|Nom du processus|Remarque et liens|
|-|-|-|-|
|Déboguer n’importe quel type d’application pris en charge sur l’ordinateur local en le démarrant à partir de Visual Studio|Le débogage F5 standard|N/A|Consultez [mise en route avec le débogueur](../debugger/getting-started-with-the-debugger.md)|
|Débogage distant d’ASP.NET 4 ou 4.5 sur un serveur IIS|Utiliser les outils à distance et l’attacher au processus|w3wp.exe|Consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Débogage distant ASP.NET Core sur un serveur IIS|Utiliser les outils à distance et l’attacher au processus|DNX.exe|Déploiement d’applications, consultez [publier sur IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pour le débogage, consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Déboguer d’autres types d’application pris en charge sur un processus de serveur|Utiliser les outils à distance (si le serveur est à distance) et l’attacher au processus|Iexplore.exe ou autres processus|Si nécessaire, utilisez le Gestionnaire des tâches pour identifier le processus. Consultez [débogage distant](../debugger/remote-debugging.md) et les sections suivantes de cette rubrique|
|Débogage à distance une application de bureau Windows|F5 et outils à distance|N/A| Consultez [débogage distant](../debugger/remote-debugging.md)|
|Une application Windows universelle (UWP), OneCore, HoloLens ou IoT de débogage à distance|Déboguer le package d’application installée|N/A|Utilisez **Debug / autres cibles de débogage / déboguer le Package d’application installé** au lieu de **Attacher au processus**|
|Déboguer une application Windows universelle (UWP), OneCore, HoloLens ou IoT que vous n’avez pas démarrer à partir de Visual Studio|Déboguer le package d’application installée|N/A|Utilisez **Debug / autres cibles de débogage / déboguer le Package d’application installé** au lieu de **Attacher au processus**|
  
> [!WARNING]
>  Pour attacher une application universelle Windows écrite en JavaScript, vous devez d’abord activer le débogage de l’application. Consultez [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) dans le Centre de développement Windows.  
  
> [!NOTE]
>  Pour que le débogueur s’attache au code écrit en C++, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) .

## <a name="what-debugger-features-can-i-use"></a>Les fonctionnalités du débogueur puis-je utiliser ?

Pour utiliser toutes les fonctionnalités du débogueur Visual Studio (par exemple, appuyer sur des points d’arrêt), le fichier exécutable doit correspondre exactement à votre source local et les symboles (autrement dit, le débogueur doit être en mesure de charger le bon [(.pbd) fichiers de symboles](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Par défaut, cela requiert une version debug.

Pour les scénarios de débogage à distance, vous devez disposer du code source une copie du code source déjà ouverte dans Visual Studio. Les binaires d’application compilé sur l’ordinateur distant doivent provenir de la même version que sur l’ordinateur local.

Dans certains scénarios de débogage locales, vous pouvez déboguer dans Visual Studio sans accès à la source si les fichiers de symboles corrects sont présents à l’application (par défaut, cela requiert une version de débogage). Pour plus d’informations, consultez [spécifier les symboles et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Pour les applications de bureau Windows, vous pouvez également déboguer l’application en cours d’exécution à l’aide du débogueur JIT (Visual Studio ouvre et vous arrêter dans le code de l’application après une erreur).

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Attacher à un processus sur un ordinateur distant  
 Pour attacher à un processus, vous devez connaître le nom du processus. Pour les applications ASP.NET qui ont été déployées sur IIS, consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou [publier sur IIS](https://docs.asp.net/en/latest/publishing/iis.html) pour les applications ASP.NET Core. Pour les autres applications, vous pourrez peut-être trouver le nom du processus dans le Gestionnaire des tâches.
  
 Quand vous utilisez la boîte de dialogue **Attacher au processus** , vous pouvez sélectionner un autre ordinateur configuré pour le débogage distant. Pour plus d’informations, consultez [débogage distant](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md). Après avoir sélectionné un ordinateur distant, vous pouvez consulter une liste des processus disponibles exécutés sur cet ordinateur et attacher le débogueur à un ou plusieurs d’entre eux pour déboguer.
  
 **Pour sélectionner un ordinateur distant :**  

1. Dans Visual Studio, sélectionnez **Déboguer / Attacher au processus**.

2.  Dans la boîte de dialogue **Attacher au processus** , sélectionnez le type de connexion approprié dans la liste **Transport** . Généralement, ce paramètre a la valeur**Défaut** .

    Le paramètre **Transport** persiste entre des sessions de débogage. 
  
3.  La zone de liste **Qualificateur** vous permet de sélectionner le nom de l’ordinateur distant à l’aide de l’une des méthodes suivantes :  
  
    1.  Tapez le nom dans la zone de liste **Qualificateur** .
    
        >**Remarque** Si, ultérieurement, vous ne peut pas se connecter en utilisant le nom de l’ordinateur distant, utilisez l’adresse IP. (Le numéro de port peut être automatiquement après avoir sélectionné le processus. Vous pouvez également l’entrer manuellement. Dans l’illustration ci-dessous, 4020 est le port par défaut pour le débogueur distant.)  
  
    2.  Cliquez sur la flèche de déroulement associée à la zone de liste **Qualificateur** , puis sélectionnez le nom de l’ordinateur dans la liste déroulante.  
  
    3.  Cliquez sur le bouton **Rechercher** en regard de la liste**Qualificateur** pour ouvrir la boîte de dialogue **Sélectionner une connexion du débogueur distant** . La boîte de dialogue **Sélectionner une connexion du débogueur distant** répertorie tous les appareils qui se trouvent sur votre sous-réseau local, et les éventuels appareils directement connectés à votre ordinateur via un câble Ethernet. Cliquez sur l’ordinateur ou l’appareil souhaité, puis sur **Sélectionner**. 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     Le paramètre **Qualificateur** persiste entre des sessions de débogage uniquement si une connexion de débogage réussie est établie avec ce qualificateur.
     
4.  Cliquez sur **Actualiser**.

      La liste **Processus disponibles** s’affiche automatiquement quand vous ouvrez la boîte de dialogue **Processus** . Les processus peuvent démarrer et s’interrompre en arrière-plan pendant que la boîte de dialogue est ouverte. Toutefois, le contenu n’est pas toujours actualisé. Vous pouvez actualiser la liste à tout moment pour visualiser la liste des processus en cours d’exécution en cliquant sur **Actualiser**. 
     
4.  Dans la boîte de dialogue **Attacher au processus** , recherchez le programme que vous voulez attacher dans la liste **Processus disponibles** .  
  
     Si le processus s’exécute sous un compte d’utilisateur différent, cochez la case **Afficher les processus de tous les utilisateurs** .
     
5.  Cliquez sur **Attacher**.  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Attacher à un processus en cours d’exécution sur l’ordinateur local  
 Pour attacher à un processus, vous devez connaître le nom du processus.  Vous pourrez peut-être trouver le nom du processus dans le Gestionnaire des tâches.  
  
1.  Dans Visual Studio, sélectionnez **Déboguer / Attacher au processus**.
  
2.  Dans la boîte de dialogue **Attacher au processus** , recherchez le programme que vous voulez attacher dans la liste **Processus disponibles** .  
  
     Si le processus s’exécute sous un compte d’utilisateur différent, cochez la case **Afficher les processus de tous les utilisateurs** .
  
3.  Dans la zone **Attacher à** , vérifiez que le type de code à déboguer est répertorié. Le paramètre par défaut **Automatique** tente de déterminer le type de code que vous souhaitez déboguer. Pour définir le type de code manuellement, procédez comme suit :  
  
    1.  Dans la zone **Attacher à** , cliquez sur **Sélectionner**.  
  
    2.  Dans la boîte de dialogue **Sélectionner le type de code** , cliquez sur **Déboguer ces types de codes** et sélectionnez les types à déboguer.  
  
    3.  Cliquez sur **OK**.  
  
4.  Cliquez sur **Attacher**.

## <a name="additional-info"></a>Informations supplémentaires

Vous pouvez attacher un débogueur à plusieurs programmes à la fois, mais un seul d’entre eux est actif dans le débogueur à un moment donné. Vous pouvez définir le programme actif dans la barre d’outils **Emplacement de débogage** ou la fenêtre **Processus** . Pour plus d’informations, consultez [Comment : définir le programme en cours](http://msdn.microsoft.com/fr-fr/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Si vous essayez d’établir un attachement à un processus appartenant à un compte d’utilisateur non fiable, une boîte de dialogue d’avertissement de sécurité s’affiche avec un message de confirmation. Pour plus d’informations, consultez [Avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou vous avez des doutes, n’attachez pas ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
Dans certains cas, lors du débogage dans une session Bureau à distance (services Terminal Server), la liste **Processus disponibles** n’affiche pas tous les processus disponibles. Si vous exécutez Visual Studio avec un compte d’utilisateur limité, la liste **Processus disponibles** n’affiche pas les processus qui s’exécutent dans la session 0, qui est utilisée pour les services et les autres processus serveur, notamment w3wp.exe. Vous pouvez résoudre le problème en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous un compte administrateur ou en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la console du serveur au lieu d’une session Terminal Server. Si aucune de ces solutions de contournement n’est possible, la troisième option consiste à attacher le débogueur au processus en exécutant `vsjitdebugger.exe -p` *ProcessId* à partir de la ligne de commande Windows. Vous pouvez déterminer l’ID de processus à l’aide de tlist.exe. Pour obtenir tlist.exe, téléchargez et installez les outils de débogage pour Windows, qui sont disponibles dans  [Téléchargements relatifs au WDK et à WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Résoudre les erreurs d’attachement  
 Quand le débogueur est attaché à un processus en cours d’exécution, le processus peut contenir un ou plusieurs types de code. Les types de code auxquels le débogueur peut s’attacher sont affichés et sélectionnés dans la boîte de dialogue **Sélectionner le type de code** .  
  
 Parfois, le débogueur peut réussir à s’attacher à un type de code, mais pas aux autres. Cela peut se produire si vous tentez d’attacher le débogueur à un processus exécuté sur un ordinateur distant. Il est possible que des composants de débogage distant soient installés pour certains types de code, mais pas pour d’autres, sur l’ordinateur distant. Cela peut également se produire si vous tentez d’attacher le débogueur à plusieurs processus pour déboguer directement la base de données. Le débogage SQL prend en charge l’attachement à un seul processus uniquement.  
  
 Si le débogueur peut être attaché à certains des types de code, mais pas à tous, un message identifie les types auxquels il n’a pas pu être attaché.  
  
 Si le débogueur parvient à s’attacher à au moins un type de code, vous pouvez procéder au débogage du processus. Vous pouvez uniquement déboguer les types de code attachés avec succès. L’exemple de message précédent indique que le type de code de script n’a pas réussi à s’attacher. Il vous sera donc impossible de déboguer le code de script se trouvant dans le processus. Le code de script continuera de s’exécuter dans le processus, mais vous ne pourrez pas définir des points d’arrêt, afficher des données ni réaliser d’autres opérations de débogage dans le script.  
  
 Si vous souhaitez des informations plus spécifiques sur l’incapacité du débogueur à s’attacher à un type de code, vous pouvez tenter d’attacher à nouveau le débogueur uniquement à ce type de code.  
  
 **Pour obtenir des informations spécifiques sur l’échec d’un type de code à attacher**  
  
1.  Procédez au détachement du processus. Dans le menu **Déboguer** , cliquez sur **Détacher tout**.  
  
2.  Rattachez le processus en sélectionnant un seul type de code.  
  
    1.  Dans la boîte de dialogue **Attacher au processus** , sélectionnez le processus dans la liste **Processus disponibles** .  
  
    2.  Cliquez sur **Sélectionner**.  
  
    3.  Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes** et le type de code qui a échoué lors de l’attachement. Effacez tout autre code.  
  
    4.  Cliquez sur **OK**. La boîte de dialogue **Sélectionner le type de code** se ferme.  
  
    5.  Dans la boîte de dialogue **Attacher au processus** , cliquez sur **Attacher**.  
  
     Cette fois-ci, l’attachement échoue entièrement et un message d’erreur spécifique s’affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)   
 [Le débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Débogage distant](../debugger/remote-debugging.md)