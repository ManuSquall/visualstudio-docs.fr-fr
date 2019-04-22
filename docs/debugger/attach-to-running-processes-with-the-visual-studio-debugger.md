---
title: Attacher au processus en cours d’exécution avec le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 04/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dad698f2ba660b6848e614f13751335894a17ae0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366404"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Attacher aux processus en cours d’exécution avec le débogueur Visual Studio
Vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution sur un ordinateur local ou distant. Une fois le processus est en cours d’exécution, sélectionnez **déboguer** > **attacher au processus** ou appuyez sur **Ctrl**+**Alt** + **P** dans Visual Studio et utiliser le **attacher au processus** boîte de dialogue pour attacher le débogueur au processus.

Vous pouvez utiliser **attacher au processus** pour déboguer des applications en cours d’exécution sur des ordinateurs locaux ou distants, déboguer plusieurs processus simultanément, de déboguer des applications qui n’ont pas été créées dans Visual Studio ou déboguer n’importe quelle application que vous n’avez pas démarré à partir de Visual Studio avec le débogueur attaché. Par exemple, si vous exécutez une application sans le débogueur et une exception, vous pouvez ensuite attacher le débogueur au processus de l’application en cours d’exécution et commencez le débogage.

> [!TIP]
> Ne savez pas s’il faut utiliser **attacher au processus** pour votre scénario de débogage ? Consultez [commune de scénarios de débogage](#BKMK_Scenarios).

##  <a name="BKMK_Attach_to_a_running_process"></a> Attacher à un processus en cours d’exécution sur votre ordinateur local

Pour vous rattacher rapidement à un processus attaché à précédemment, consultez [rattacher à un processus](#BKMK_reattach).

Pour déboguer un processus sur un ordinateur distant, consultez [attacher à un processus sur un ordinateur distant](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Pour attacher à un processus sur votre ordinateur local :**

1. Dans Visual Studio, sélectionnez **déboguer** > **attacher au processus** (ou appuyez sur **Ctrl**+**Alt** + **P**) pour ouvrir la **attacher au processus** boîte de dialogue.

   **Type de connexion** doit être défini sur **par défaut**. **Cible de la connexion** doit être le nom de votre ordinateur local.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Dans le **processus disponibles** liste, recherchez et sélectionnez l’ou les processus que vous voulez attacher.

   - Pour sélectionner rapidement un processus, tapez son nom ou la première lettre de la **filtrer les processus** boîte.

   - Si vous ne connaissez pas le nom du processus, parcourez la liste, ou consultez [commune de scénarios de débogage](#BKMK_Scenarios) pour certains noms de processus courants.

   >[!TIP]
   >Les processus peuvent démarrer et arrêter dans l’arrière-plan, tandis que le **attacher au processus** boîte de dialogue est ouverte, la liste des processus en cours peut ne pas être toujours en cours. Vous pouvez sélectionner **Actualiser** à tout moment pour consulter la liste actuelle.

3. Dans le **attacher à** champ, vérifiez que le type de code que vous souhaitez déboguer est répertorié. La valeur par défaut **automatique** définissant fonctionne pour la plupart des types d’applications.

   Pour sélectionner manuellement les types de code :
   1. Cliquez sur **Sélectionner**.
   1. Dans le **sélectionner le Type de Code** boîte de dialogue, sélectionnez **déboguer ces types de codes**.
   1. Sélectionnez les types de code que vous souhaitez déboguer.
   1. Sélectionnez **OK**.

4. Sélectionnez **attacher**.

>[!NOTE]
>Vous pouvez être connecté à plusieurs applications pour le débogage, mais qu’une seule application est active dans le débogueur à la fois. Vous pouvez configurer l’application active dans Visual Studio **emplacement de débogage** barre d’outils ou **processus** fenêtre.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Attacher à un processus sur un ordinateur distant

Vous pouvez également sélectionner un ordinateur distant dans le **attacher au processus** boîte de dialogue Afficher la liste des processus disponibles exécutés sur cet ordinateur et d’attachement à un ou plusieurs des processus de débogage. Le débogueur distant (*msvsmon.exe*) doit être en cours d’exécution sur l’ordinateur distant. Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).

Pour des instructions détaillées pour le débogage des applications ASP.NET qui ont été déployées sur IIS, consultez [débogage ASP.NET sur un ordinateur IIS distant à distance](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Pour attacher à un processus en cours d’exécution sur un ordinateur distant :**

1. Dans Visual Studio, sélectionnez **déboguer** > **attacher au processus** (ou appuyez sur **Ctrl**+**Alt** + **P**) pour ouvrir la **attacher au processus** boîte de dialogue.

2. **Type de connexion** doit être **par défaut** pour la plupart des cas. Dans le **cible de la connexion** , sélectionnez l’ordinateur distant, en utilisant l’une des méthodes suivantes :

   - Sélectionnez la flèche déroulante à côté **cible de la connexion**, puis sélectionnez le nom d’ordinateur dans la liste déroulante.
   - Tapez le nom d’ordinateur dans le **cible de la connexion** zone et appuyez sur **entrée**.

     Vérifiez que Visual Studio ajoute le port requis pour le nom d’ordinateur, qui apparaît dans le format :  **\<nom_ordinateur_distant > : port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Si vous ne pouvez pas vous connecter en utilisant le nom de l’ordinateur distant, essayez d’utiliser l’adresse IP et l’adresse du port (par exemple, `123.45.678.9:4022`). 4024 est le port par défaut pour le débogueur distant Visual Studio 2019 x64. Pour d’autres affectations de port débogueur distant, consultez [affectations de port de débogueur distant](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Si vous ne pouvez pas vous connecter en utilisant le nom de l’ordinateur distant, essayez d’utiliser l’adresse IP et l’adresse du port (par exemple, `123.45.678.9:4022`). 4022 est le port par défaut pour le débogueur distant Visual Studio 2017 x64. Pour d’autres affectations de port débogueur distant, consultez [affectations de port de débogueur distant](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Sélectionnez le **trouver** situé en regard du **cible de la connexion** boîte pour ouvrir la **connexions à distance** boîte de dialogue. Le **connexions à distance** boîte de dialogue répertorie tous les appareils qui se trouvent sur votre sous-réseau local ou directement attaché à votre ordinateur. Vous devrez peut-être [ouvrir le port UDP 3702](../debugger/remote-debugger-port-assignments.md) sur le serveur pour détecter des appareils à distance. Sélectionnez l’ordinateur ou un appareil de votre choix, puis cliquez sur **sélectionnez**.

   > [!NOTE]
   > Le **type de connexion** paramètre persiste entre des sessions de débogage. Le **cible de la connexion** paramètre persiste entre des sessions de débogage uniquement si une connexion de débogage réussie s’est produite avec cette cible.

3. Cliquez sur **Actualiser** pour remplir le **processus disponibles** liste.

    >[!TIP]
    >Les processus peuvent démarrer et arrêter dans l’arrière-plan, tandis que le **attacher au processus** boîte de dialogue est ouverte, la liste des processus en cours peut ne pas être toujours en cours. Vous pouvez sélectionner **Actualiser** à tout moment pour consulter la liste actuelle.

4. Dans le **processus disponibles** liste, recherchez et sélectionnez l’ou les processus que vous voulez attacher.

   - Pour sélectionner rapidement un processus, tapez son nom ou la première lettre de la **filtrer les processus** boîte.

   - Si vous ne connaissez pas le nom du processus, parcourez la liste, ou consultez [commune de scénarios de débogage](#BKMK_Scenarios) pour certains noms de processus courants.

   - Pour rechercher les processus qui s’exécutent sous tous les comptes d’utilisateur, sélectionnez le **afficher les processus de tous les utilisateurs** case à cocher.

     >[!NOTE]
     >Si vous essayez d’établir un attachement à un processus appartenant à un compte d’utilisateur non fiable, une boîte de dialogue d’avertissement de sécurité s’affiche avec un message de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, n’attachez pas ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Dans le **attacher à** champ, vérifiez que le type de code que vous souhaitez déboguer est répertorié. La valeur par défaut **automatique** définissant fonctionne pour la plupart des types d’applications.

   Pour sélectionner manuellement les types de code :
   1. Cliquez sur **Sélectionner**.
   1. Dans le **sélectionner le Type de Code** boîte de dialogue, sélectionnez **déboguer ces types de codes**.
   1. Sélectionnez les types de code que vous souhaitez déboguer.
   1. Sélectionnez **OK**.

6. Sélectionnez **attacher**.

>[!NOTE]
>Vous pouvez être connecté à plusieurs applications pour le débogage, mais qu’une seule application est active dans le débogueur à la fois. Vous pouvez configurer l’application active dans Visual Studio **emplacement de débogage** barre d’outils ou **processus** fenêtre.

Dans certains cas, lorsque vous déboguez dans une session Bureau à distance (Terminal Services), le **processus disponibles** liste affichera tous les processus disponibles. Si vous exécutez Visual Studio en tant qu’utilisateur disposant d’un compte d’utilisateur limité, la **processus disponibles** liste n’affiche les processus qui s’exécutent dans la Session 0. La session 0 est utilisée pour les services et les autres processus serveur, y compris *w3wp.exe*. Vous pouvez résoudre le problème en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous un compte administrateur ou en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la console du serveur au lieu d’une session Terminal Server.

Si aucune de ces solutions n’est possible, la troisième option consiste à attacher le débogueur au processus en exécutant `vsjitdebugger.exe -p <ProcessId>` à partir de la ligne de commande Windows. Vous pouvez déterminer l’ID de processus à l’aide *tlist.exe*. Pour obtenir *tlist.exe*, téléchargez et installez les outils de débogage pour Windows, qui sont disponibles dans [Téléchargements relatifs au WDK et à WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Rattacher à un processus

Vous pouvez rattacher rapidement aux processus qui vous ont été précédemment attaché en choisissant **déboguer** > **rattacher au processus** (**MAJ** + **Alt**+**P**). Lorsque vous choisissez cette commande, le débogueur va immédiatement tenter d’attacher au dernier processus que vous avez attaché à par la première tentative correspond à l’ID de processus précédente et si cette tentative échoue, en mettant en correspondance pour le précédent nom du processus. Si aucune correspondance n’est trouvée, ou si plusieurs processus portent le même nom, le **attacher au processus** boîte de dialogue s’ouvre, vous pouvez sélectionner le processus correct.

> [!NOTE]
> Le **rattacher au processus** commande est disponible à partir de Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Scénarios de débogage courants

Pour vous aider à déterminer s’il faut utiliser **attacher au processus** et les processus à attacher, le tableau suivant présente quelques scénarios de débogage courantes, avec des liens vers des instructions plus détaillées le cas échéant. (La liste n’est pas exhaustive.)

Pour certains types d’applications, telles que des applications de l’application universelle Windows (UWP), ne pas attacher directement à un nom de processus, mais utiliser le **déboguer le Package d’application installé** l’option de menu dans Visual Studio à la place (voir tableau).

Pour que le débogueur s’attache au code écrit en C++, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Débogage de script côté client, le débogage de script doit être activé dans le navigateur. Pour le débogage de script côté client sur Chrome, choisissez **kit Web** en tant que le type de code et, selon votre type d’application, vous devrez peut-être fermer toutes les instances de Chrome et démarrer le navigateur en mode débogage (type `chrome.exe --remote-debugging-port=9222` à partir d’une ligne de commande).

Pour sélectionner rapidement un processus en cours d’exécution à attacher, dans Visual Studio, tapez **Ctrl**+**Alt**+**P**, puis tapez la première lettre de la nom du processus.

|Scénario|Déboguer (méthode)|Nom du processus|Notes de publication et des liens|
|-|-|-|-|
|Débogage distant ASP.NET 4 ou 4.5 sur un serveur IIS|Utiliser les outils distants et **attacher au processus**|*w3wp.exe*|Consultez [débogage ASP.NET sur un ordinateur IIS distant à distance](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Débogage à distance ASP.NET Core sur un serveur IIS|Utiliser les outils distants et **attacher au processus**|*dotnet.exe*|Déploiement d’applications, consultez [publier sur IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pour le débogage, consultez [distant débogage ASP.NET Core sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Déboguer un script côté client sur un serveur IIS local, pour les types d’application pris en charge |Utilisez **attacher au processus**|*chrome.exe*, *MicrosoftEdgeCP.exe*, ou *iexplore.exe*|Débogage de script doit être activé. Pour Chrome, vous devez également exécuter Chrome en mode débogage et sélectionnez **code Webkit** dans le **attacher à** champ.|
|Déboguer une application c#, Visual Basic ou C++ sur l’ordinateur local|Utilisez l’outil de débogage standard (**F5**) ou **attacher au processus**|*\<appname>.exe*|Dans la plupart des scénarios, utiliser le débogage standard et non **attacher au processus**.|
|Débogage à distance une application de bureau Windows|Outils à distance|N/A| Consultez [à distance déboguer une application c# ou Visual Basic](../debugger/remote-debugging-csharp.md) ou [à distance déboguer une application C++](../debugger/remote-debugging-cpp.md)|
|Déboguer une application ASP.NET sur l’ordinateur local après avoir démarré l’application sans le débogueur|Utilisez **attacher au processus**|*iiexpress.exe*|Cela peut être utile pour rendre votre application à charger plus rapidement, telles que (par exemple) lors du profilage. |
|Déboguer d’autres types d’application pris en charge sur un processus de serveur|Si server est distant, utilisez les outils à distance, et **attacher au processus**|*chrome.exe*, *iexplore.exe*, ou d’autres processus|Si nécessaire, utilisez le moniteur de ressources pour aider à identifier le processus. Consultez [Débogage à distance](../debugger/remote-debugging.md).|
|Une application universelle Windows (UWP), OneCore, HoloLens, IoT application ou de débogage à distance|Déboguer un package d’application installé|N/A|Consultez [déboguer un package d’application installé](debug-installed-app-package.md) au lieu d’utiliser **attacher au processus**|
|Déboguer une application universelle Windows (UWP), OneCore, HoloLens, IoT application ou que vous n’avez pas démarré à partir de Visual Studio|Déboguer un package d’application installé|N/A|Consultez [déboguer un package d’application installé](debug-installed-app-package.md) au lieu d’utiliser **attacher au processus**|

## <a name="use-debugger-features"></a>Utiliser les fonctionnalités du débogueur

Pour utiliser toutes les fonctionnalités du débogueur Visual Studio (par exemple, en appuyant sur des points d’arrêt) lors de l’attachement à un processus, l’application doit correspondre exactement à votre code source local et des symboles. Autrement dit, le débogueur doit être en mesure de charger le bon [de symboles (.pdb) fichiers](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Par défaut, cela requiert une version debug.

Pour les scénarios de débogage à distance, vous devez disposer du code source (ou une copie du code source) déjà ouvert dans Visual Studio. Les fichiers binaires d’application compilée sur l’ordinateur distant doivent provenir de la même build que sur l’ordinateur local.

Dans certains scénarios de débogage locales, vous pouvez déboguer dans Visual Studio sans accès à la source si les fichiers de symboles corrects sont présents à l’application. Par défaut, cela requiert une version debug. Pour plus d’informations, consultez [spécifier les symboles et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

##  <a name="BKMK_Troubleshoot_attach_errors"></a> Résoudre les erreurs d’attachement
 Quand le débogueur est attaché à un processus en cours d’exécution, le processus peut contenir un ou plusieurs types de code. Les types de code auxquels le débogueur peut s’attacher sont affichés et sélectionnés dans la boîte de dialogue **Sélectionner le type de code** .

 Parfois, le débogueur peut réussir à s’attacher à un type de code, mais pas aux autres. Cela peut se produire si vous tentez d’attacher le débogueur à un processus exécuté sur un ordinateur distant. Il est possible que des composants de débogage distant soient installés pour certains types de code, mais pas pour d’autres, sur l’ordinateur distant. Cela peut également se produire si vous tentez d’attacher le débogueur à plusieurs processus pour déboguer directement la base de données. Le débogage SQL prend en charge l’attachement à un seul processus uniquement.

 Si le débogueur est en mesure de joindre à certains, mais pas tous les types de code, vous voyez un message identifiant les types d’échec d’attachement.

 Si le débogueur parvient à s’attacher à au moins un type de code, vous pouvez procéder au débogage du processus. Vous pouvez uniquement déboguer les types de code attachés avec succès. Le code non attaché dans le processus s’exécutera, mais vous ne pourrez pas définir des points d’arrêt, afficher les données ou effectuer d’autres opérations de débogage de ce code.

 Si vous souhaitez des informations plus spécifiques sur l’incapacité du débogueur à attacher à un type de code, essayez de rattacher à uniquement ce type de code.

 **Pour connaître les raisons de l’échec de l’attachement d’un type de code :**

1.  Procédez au détachement du processus. Sur le **déboguer** menu, sélectionnez **Détacher tout**.

1.  Rattacher au processus, en sélectionnant le type de code qui n’a pas pu attacher.

    1.  Dans la boîte de dialogue **Attacher au processus**, sélectionnez le processus dans la liste **Processus disponibles**.

    2.  Sélectionnez **sélectionnez**.

    3.  Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes** et le type de code qui a échoué lors de l’attachement. Désélectionnez les autres types de code.

    4.  Sélectionnez **OK**.

    5.  Dans le **attacher au processus** boîte de dialogue, sélectionnez **attacher**.

    Cette fois-ci, l’attachement échoue entièrement et un message d’erreur spécifique s’affiche.

## <a name="see-also"></a>Voir aussi

- [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)
- [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Débogage distant](../debugger/remote-debugging.md)