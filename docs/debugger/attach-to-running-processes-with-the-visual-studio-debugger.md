---
title: Attachez-vous aux processus d’exécution avec le débagénaire . Microsoft Docs
ms.custom: seodec18
ms.date: 04/14/2020
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
ms.openlocfilehash: 075f5b0df703e31ea265085f422567a4fb5298a4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385492"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Attacher aux processus en cours d’exécution avec le débogueur Visual Studio
Vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution sur un ordinateur local ou distant. Une fois le processus en cours d’exécution, sélectionnez **Debug** > **Attach to Process** ou appuyez sur **Ctrl**+**Alt**+**P** dans Visual Studio, et utilisez le dialogue Attach to **Process** pour attacher le débbugger au processus.

Vous pouvez utiliser **Attach to Process** pour déboguer des applications en cours d’exécution sur des ordinateurs locaux ou distants, déboguer plusieurs processus simultanément, déboguer des applications qui n’ont pas été créées dans Visual Studio, ou déboguer toute application que vous n’avez pas commencé à partir de Visual Studio avec le débbugger attaché. Par exemple, si vous exécutez une application sans le débbugger et appuyez sur une exception, vous pouvez alors joindre le débbugger au processus d’exécution de l’application et commencer à débogage.

> [!TIP]
> Vous ne savez pas s’il faut utiliser **Attach to Process** pour votre scénario de débogage? Voir [les scénarios de débogage communs](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Attachez-vous à un processus d’exécution sur votre machine locale

Pour rattacher rapidement à un processus que vous avez attaché à précédemment, voir [Reattach à un processus](#BKMK_reattach).

Pour déboiffer un processus sur un ordinateur distant, voir [Joindre à un processus sur un ordinateur distant](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Pour déboiffer un processus .NET Core sur un conteneur Linux Docker, voir [Attach to a Linux Docker container](#BKMK_Linux_Docker_Attach).
::: moniker-end

**Pour s’attacher à un processus sur votre ordinateur local :**

1. Dans Visual Studio, sélectionnez **Debug** > **Attach to Process** (ou appuyez sur **Ctrl**+**Alt**+**P**) pour ouvrir la boîte de dialogue Attach to **Process.**

   **Le type de connexion** doit être réglé **en défaut**. **La cible de connexion** doit être votre nom de machine local.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Dans la liste **des processus disponibles,** trouvez et sélectionnez le processus ou les processus que vous souhaitez joindre.

   - Pour sélectionner rapidement un processus, tapez son nom ou sa première lettre dans la boîte **de processus de filtre.**

   - Si vous ne connaissez pas le nom du processus, parcourez la liste ou voyez [des scénarios de débogage courants](#BKMK_Scenarios) pour certains noms de processus communs.

   >[!TIP]
   >Les processus peuvent démarrer et s’arrêter en arrière-plan pendant que la boîte de dialogue **Attach to Process** est ouverte, de sorte que la liste des processus en cours d’exécution peut ne pas toujours être à jour. Vous pouvez sélectionner **Refresh** à tout moment pour voir la liste actuelle.

3. Dans le **champ Attach to** field, assurez-vous que le type de code que vous prévoyez de déboiffer est répertorié. Le paramètre **automatique** par défaut fonctionne pour la plupart des types d’applications.

   Pour sélectionner manuellement les types de code :
   1. Cliquez sur **Sélectionner**.
   1. Dans la boîte de dialogue **Select Code Type,** sélectionnez **Debug ces types de code**.
   1. Sélectionnez les types de code que vous souhaitez déboiffer.
   1. Sélectionnez **OK**.

4. Sélectionnez **Attacher**.

>[!NOTE]
>Vous pouvez être attaché à plusieurs applications pour débogage, mais une seule application est active dans le débbugger à la fois. Vous pouvez configurer l’application active dans la barre d’outils Visual Studio **Debug Location** ou la fenêtre **Processes.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Attacher à un processus sur un ordinateur distant

Vous pouvez également sélectionner un ordinateur distant dans la boîte de dialogue **Attach to Process,** afficher une liste des processus disponibles en cours d’exécution sur cet ordinateur, et s’attacher à un ou plusieurs des processus de débogage. Le débbuggeur à distance (*msvsmon.exe*) doit être en cours d’exécution sur l’ordinateur distant. Pour plus d’informations, voir [Débugging à distance](../debugger/remote-debugging.md).

Pour des instructions plus complètes pour débogage ASP.NET applications qui ont été déployées à l’IIS, voir [à distance débogage ASP.NET sur un ordinateur à distance IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Pour s’attacher à un processus d’exécution sur un ordinateur distant :**

1. Dans Visual Studio, sélectionnez **Debug** > **Attach to Process** (ou appuyez sur **Ctrl**+**Alt**+**P**) pour ouvrir la boîte de dialogue Attach to **Process.**

2. **Le type de connexion** doit être **par défaut** pour la plupart des cas. Dans la boîte **cible Connection,** sélectionnez l’ordinateur distant, en utilisant l’une des méthodes suivantes :

   - Sélectionnez la flèche de décrochage à côté de **la cible De connexion**et sélectionnez le nom de l’ordinateur de la liste d’abandon.
   - Tapez le nom de l’ordinateur dans la boîte **cible Connection** et appuyez **sur Entrez**.

     Vérifiez que Visual Studio ajoute le port requis au nom de l’ordinateur, qui apparaît dans le format: ** \<nom d’ordinateur à distance>:port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Si vous ne pouvez pas vous connecter à l’aide du nom `123.45.678.9:4022`de l’ordinateur distant, essayez d’utiliser l’adresse IP et port (par exemple, ). 4024 est le port par défaut pour le Visual Studio 2019 x64 débugger à distance. Pour d’autres affectations portuaires de débogénaires à distance, voir [les affectations portuaires de débbugger à distance](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Si vous ne pouvez pas vous connecter à l’aide du nom `123.45.678.9:4022`de l’ordinateur distant, essayez d’utiliser l’adresse IP et port (par exemple, ). 4022 est le port par défaut pour le Visual Studio 2017 x64 débugger à distance. Pour d’autres affectations portuaires de débogénaires à distance, voir [les affectations portuaires de débbugger à distance](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Sélectionnez le bouton **Trouver** à côté de la boîte **cible Connection** pour ouvrir la boîte de dialogue **Remote Connections.** La boîte de dialogue **Remote Connections** répertorie tous les appareils qui sont sur votre sous-réseau local ou directement attachés à votre ordinateur. Vous devrez peut-être [ouvrir le port UDP 3702](../debugger/remote-debugger-port-assignments.md) sur le serveur pour découvrir des appareils distants. Sélectionnez l’ordinateur ou l’appareil que vous voulez, puis cliquez sur **Sélectionnez**.

   > [!NOTE]
   > Le réglage **de type Connexion** persiste entre les sessions de débogage. **L’établissement de la cible Connection** persiste entre les séances de débogage seulement si une raccordement réussi de débogage s’est produite avec cette cible.

3. Cliquez **sur Refresh** pour remplir la liste des processus **disponibles.**

    >[!TIP]
    >Les processus peuvent démarrer et s’arrêter en arrière-plan pendant que la boîte de dialogue **Attach to Process** est ouverte, de sorte que la liste des processus en cours d’exécution peut ne pas toujours être à jour. Vous pouvez sélectionner **Refresh** à tout moment pour voir la liste actuelle.

4. Dans la liste **des processus disponibles,** trouvez et sélectionnez le processus ou les processus que vous souhaitez joindre.

   - Pour sélectionner rapidement un processus, tapez son nom ou sa première lettre dans la boîte **de processus de filtre.**

   - Si vous ne connaissez pas le nom du processus, parcourez la liste ou voyez [des scénarios de débogage courants](#BKMK_Scenarios) pour certains noms de processus communs.

   - Pour trouver des processus en cours d’exécution sous tous les comptes d’utilisateurs, sélectionnez les processus Afficher à partir de la case à cocher **de tous les utilisateurs.**

     >[!NOTE]
     >Si vous essayez d’établir un attachement à un processus appartenant à un compte d’utilisateur non fiable, une boîte de dialogue d’avertissement de sécurité s’affiche avec un message de confirmation. Pour plus d’informations, voir [Avertissement de sécurité : s’attacher à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou si vous n’êtes pas sûr, ne vous attachez pas à ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Dans le **champ Attach to** field, assurez-vous que le type de code que vous prévoyez de déboiffer est répertorié. Le paramètre **automatique** par défaut fonctionne pour la plupart des types d’applications.

   Pour sélectionner manuellement les types de code :
   1. Cliquez sur **Sélectionner**.
   1. Dans la boîte de dialogue **Select Code Type,** sélectionnez **Debug ces types de code**.
   1. Sélectionnez les types de code que vous souhaitez déboiffer.
   1. Sélectionnez **OK**.

6. Sélectionnez **Attacher**.

>[!NOTE]
>Vous pouvez être attaché à plusieurs applications pour débogage, mais une seule application est active dans le débbugger à la fois. Vous pouvez configurer l’application active dans la barre d’outils Visual Studio **Debug Location** ou la fenêtre **Processes.**

Dans certains cas, lorsque vous déboillez dans une session Remote Desktop (Terminal Services), la liste **des processus disponibles** n’affiche pas tous les processus disponibles. Si vous exécutez Visual Studio en tant qu’utilisateur qui a un compte utilisateur limité, la liste **des processus disponibles** n’affichera pas les processus qui s’exécutent dans la session 0. Session 0 est utilisé pour les services et autres processus de serveur, y compris *w3wp.exe*. Vous pouvez résoudre le problème en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous un compte administrateur ou en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la console du serveur au lieu d’une session Terminal Server.

Si aucune de ces solutions n’est possible, la troisième option consiste à attacher le débogueur au processus en exécutant `vsjitdebugger.exe -p <ProcessId>` à partir de la ligne de commande Windows. Vous pouvez déterminer l’ID processus à l’aide *de tlist.exe*. Pour obtenir *tlist.exe*, téléchargez et installez les outils de débogage pour Windows, qui sont disponibles dans [Téléchargements relatifs au WDK et à WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Attachez-vous à un processus .NET Core fonctionnant sur Linux à l’aide de SSH

Pour plus d’informations, voir [Remote debug .NET Core fonctionnant sur Linux à l’aide de SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Attachez-vous à un processus fonctionnant sur un conteneur Linux Docker

Vous pouvez attacher le debugger Visual Studio à un processus en cours d’exécution dans un conteneur Linux .NET Core Docker sur votre machine locale ou distante à l’aide de la boîte de dialogue **Attach to Process.**

> [!IMPORTANT]
> Pour utiliser cette fonctionnalité, vous devez installer la charge de travail de développement de plateformes croisées .NET Core et avoir un accès local au code source.

**Pour s’attacher à un processus d’exécution dans un conteneur Linux Docker :**

1. Dans Visual Studio, sélectionnez **Debug > Attach to Process (CTRL-ALT-P)** pour ouvrir la boîte de dialogue **Attach to Process.**

![Joindre au menu de processus](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Définissez le **type de connexion** à Docker **(Linux Container)**.
3. Sélectionnez **Trouver...** pour définir la **cible de connexion** via la boîte de dialogue Select Docker **Container.**

    Vous pouvez déboiffer un processus de conteneur Docker localement ou à distance.
    
    **Pour déboiffer localement un processus de conteneur Docker :**
    1. Définir **Docker CLI hôte** de Local **Machine**.
    1. Sélectionnez un conteneur en cours d’exécution à attacher à partir de la liste et appuyez **sur OK**.
    
    ![Sélectionnez Le menu Conteneur Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Pour déboiffer à distance un processus de conteneur Docker :**
    
    > [!NOTE] 
    > Il existe deux options pour se connecter à distance à un processus d’exécution dans un conteneur Docker. La première option, pour utiliser SSH, est idéale si vous n’avez pas d’outils Docker installés sur votre machine locale.  Si vous avez des outils Docker installés localement et que vous avez un démon Docker qui est configuré pour accepter les demandes à distance, essayez la deuxième option, à l’aide d’un daemon Docker.

    1. ***Pour vous connecter à une machine à distance via SSH :***
        1. Sélectionnez **Ajouter...** pour vous connecter à un système distant.<br/>
        ![Connectez-vous à un système distant](../debugger/media/connect-remote-system.png "Connectez-vous à un système distant")
        1. Sélectionnez un conteneur en cours d’exécution à attacher après la connexion à la SSH ou daemon avec succès et frapper **OK**.

    
    1. ***Pour fixer la cible à un conteneur distant exécutant un processus via un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Spécifiez l’adresse daemon (c.-à-d. via TCP, IP, etc.) sous **l’hôte Docker (Facultatif)** et cliquez sur le lien de rafraîchissement.
        1. Sélectionnez un conteneur en cours d’exécution à attacher après la connexion au daemon avec succès et appuyez **sur OK**.

4. Choisissez le processus de conteneur correspondant parmi la liste des **processus disponibles** et **sélectionnez Attach** pour commencer à déboguer votre processus de conteneurS CMD dans Visual Studio!

    ![Menu Docker Attach complété](../debugger/media/docker-attach-complete.png "Menu Linux Docker Attach complété")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Attachez-vous à un processus fonctionnant sur un conteneur Windows Docker

Vous pouvez attacher le débbugger Visual Studio à un processus en cours d’exécution dans un conteneur Windows Docker sur votre machine locale à l’aide de la boîte de dialogue **Attach to Process.**

> [!IMPORTANT]
> Pour utiliser cette fonctionnalité avec un processus .NET Core, vous devez installer la charge de travail de développement de plateformes croisées .NET Core et avoir un accès local au code source.

**Pour s’attacher à un processus d’exécution dans un conteneur Windows Docker :**

1. Dans Visual Studio, sélectionnez **Debug > Attach to Process** (ou **CTRL-ALT-P**) pour ouvrir la boîte de dialogue **Attach to Process.**

   ![Joindre au menu de processus](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Définissez le **type de connexion** à Docker **(Windows Container)**.
3. Sélectionnez **Trouver...** pour définir la **cible de connexion** à l’aide de la boîte de dialogue Select Docker **Container.**

    > [!IMPORTANT]
    > Le processus cible doit avoir la même architecture de processeur que le conteneur Docker Windows sur lequel il fonctionne.
    
   La configuration de la cible vers un conteneur distant via SSH n’est actuellement pas disponible et ne peut être effectuée qu’à l’aide d’un démon Docker.
    
    ***Pour fixer la cible à un conteneur distant exécutant un processus via un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Spécifiez l’adresse daemon (c.-à-d. via TCP, IP, etc.) sous **l’hôte Docker (Facultatif)** et cliquez sur le lien de rafraîchissement. 

    1. Sélectionnez un conteneur en cours d’exécution à joindre après connexion au daemon avec succès et choisissez OK.
    
4. Choisissez le processus de conteneur correspondant parmi la liste des **processus disponibles** et **sélectionnez Attach** pour commencer à déboguer votre processus de conteneur C.

    ![Menu Docker Attach complété](../debugger/media/docker-attach-complete-windows.png "Menu Complet de Windows Docker Attach")
    

5.  Choisissez le processus de conteneur correspondant parmi la liste des processus disponibles et choisissez **Attach** pour commencer à déboguer votre processus de conteneur C.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Rattacher à un processus

Vous pouvez rapidement réattacher aux processus auxquels vous étiez précédemment attaché en choisissant **Debug** > **Reattach à Process** (**Shift**+**Alt**+**P**). Lorsque vous choisissez cette commande, le débbuggeur essaie immédiatement de s’attacher aux derniers processus auxquels vous vous êtes attaché en essayant d’abord de faire correspondre l’ID de processus précédent et si cela échoue, en faisant correspondre le nom du processus précédent. Si aucune correspondance n’est trouvée, ou si plusieurs processus portent le même nom, la boîte de dialogue **Attach to Process** s’ouvrira afin que vous puissiez sélectionner le processus correct.

> [!NOTE]
> La commande **Reattach to Process** est disponible à partir de Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Scénarios de débogage courants

Pour vous aider à déterminer s’il y a lieu d’utiliser **Attach to Process** et à quel processus vous attacher, le tableau suivant affiche quelques scénarios courants de débogage, avec des liens vers plus d’instructions lorsque disponible. (La liste n’est pas exhaustive.)

Pour certains types d’applications, comme les applications Universal Windows App (UWP), vous ne vous fixez pas directement à un nom de processus, mais utilisez l’option de menu **Debug Installed App Package** dans Visual Studio à la place (voir tableau).

Pour que le débogueur s’attache au code écrit en C++, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Pour le débogage de script côté client, le débogage de script doit être activé dans le navigateur. Pour débogage de script côté client sur Chrome, choisissez **JavaScript (Chrome)** ou **JavaScript (Microsoft Edge - Chromium)** comme type de code, et selon votre `chrome.exe --remote-debugging-port=9222` type d’application, vous devrez peut-être fermer toutes les instances Chrome et démarrer le navigateur en mode débogage (type à partir d’une ligne de commande). Dans les versions précédentes de Visual Studio, le débbugger script pour Chrome était **kit Web**.

Pour sélectionner rapidement un processus d’exécution à joindre, dans Visual Studio, **tapez Ctrl**+**Alt**+**P**, puis tapez la première lettre du nom du processus.

|Scénario|Méthode Debug|Nom du processus|Notes et liens|
|-|-|-|-|
|Débogé à distance ASP.NET 4 ou 4,5 sur un serveur IIS|Utiliser des outils distants et **s’attacher au processus**|*w3wp.exe*|Voir [les ASP.NET de débogage à distance sur un ordinateur IIS à distance](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Débogé à distance ASP.NET Core sur un serveur IIS|Utiliser des outils distants et **s’attacher au processus**|*w3wp.exe* ou *dotnet.exe*|À partir de .NET Core 3, le processus *w3wp.exe* est utilisé pour le [modèle d’hébergement in-app](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models)par défaut . Pour le déploiement de l’application, voir [Publier sur IIS](/aspnet/core/host-and-deploy/iis/). Pour plus d’informations, voir [le débogage à distance ASP.NET Core sur un ordinateur IIS à distance](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Debug script côté client sur un serveur LOCAL IIS, pour les types d’applications pris en charge |Utiliser **l’attachement au processus**|*chrome.exe*, *MicrosoftEdgeCP.exe*, ou *iexplore.exe*|La débogage de script doit être activée. Pour Chrome, vous devez également exécuter Chrome `chrome.exe --remote-debugging-port=9222` en mode débogé (type à partir d’une ligne de commande) et sélectionner **JavaScript (Chrome)** dans le **Attach to** field.|
|Débogé d’une application de base visuelle, visuelle ou C sur la machine locale|Utilisez soit le débogage standard (**F5**) ou **attachez-vous au processus**|*\<appname>.exe*|Dans la plupart des scénarios, utilisez le débogage standard et ne pas **joindre au processus**.|
|Débogé à distance d’une application de bureau Windows|Outils à distance|N/A| Voir [Remote debug a C’ou Visual Basic app](../debugger/remote-debugging-csharp.md) or Remote [debug a C 'app](../debugger/remote-debugging-cpp.md)|
|Debug .NET Core sur Linux|Utiliser **l’attachement au processus**|*dotnet.exe*|Pour utiliser SSH, voir [Remote debug .NET Core fonctionnant sur Linux à l’aide de SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Débogé d’une application ASP.NET sur la machine locale après avoir commencé l’application sans le débbugger|Utiliser **l’attachement au processus**|*iiexpress.exe*|Cela peut être utile pour rendre votre charge d’application plus rapide, comme (par exemple) lors du profilage. |
|Debug autres types d’applications pris en charge sur un processus serveur|Si le serveur est distant, utilisez des outils distants et **attachez-vous au processus**|*chrome.exe*, *iexplore.exe*, ou d’autres processus|Si nécessaire, utilisez Resource Monitor pour vous aider à identifier le processus. Consultez [Débogage à distance](../debugger/remote-debugging.md).|
|Débogé à distance d’une application Windows Universelle (UWP), OneCore, HoloLens ou IoT|Déboguer un package d’application installé|N/A|Voir [Debug un package d’application installé](debug-installed-app-package.md) au lieu d’utiliser **Attach to Process**|
|Debug une application Windows Universelle (UWP), OneCore, HoloLens, ou IoT app que vous n’avez pas commencé à partir de Visual Studio|Déboguer un package d’application installé|N/A|Voir [Debug un package d’application installé](debug-installed-app-package.md) au lieu d’utiliser **Attach to Process**|

## <a name="use-debugger-features"></a>Utilisez des fonctionnalités de débagé

Pour utiliser toutes les fonctionnalités du débbugger Visual Studio (comme frapper les points d’arrêt) lors de l’attachement à un processus, l’application doit exactement correspondre à votre source locale et symboles. C’est-à-dire, le débbugger doit être en mesure de charger le symbole correct [(.pdb) fichiers](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Par défaut, cela nécessite une construction de débogé.

Pour les scénarios de débogage à distance, vous devez avoir le code source (ou une copie du code source) déjà ouvert dans Visual Studio. Les binaires d’application compilés sur la machine à distance doivent provenir de la même construction que sur la machine locale.

Dans certains scénarios locaux de débogage, vous pouvez débogage dans Visual Studio sans accès à la source si les fichiers symboles corrects sont présents avec l’application. Par défaut, cela nécessite une construction de débogé. Pour plus d’informations, voir [Spécifier les fichiers symbole et source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Résoudre les erreurs d’attachement
 Quand le débogueur est attaché à un processus en cours d’exécution, le processus peut contenir un ou plusieurs types de code. Les types de code auxquels le débogueur peut s’attacher sont affichés et sélectionnés dans la boîte de dialogue **Sélectionner le type de code** .

 Parfois, le débogueur peut réussir à s’attacher à un type de code, mais pas aux autres. Cela peut se produire si vous tentez d’attacher le débogueur à un processus exécuté sur un ordinateur distant. Il est possible que des composants de débogage distant soient installés pour certains types de code, mais pas pour d’autres, sur l’ordinateur distant. Cela peut également se produire si vous tentez d’attacher le débogueur à plusieurs processus pour déboguer directement la base de données. Le débogage SQL prend en charge l’attachement à un seul processus uniquement.

 Si le débbuggeur est capable de s’attacher à certains types de code, mais pas tous, vous voyez un message identifiant quels types n’ont pas attaché.

 Si le débogueur parvient à s’attacher à au moins un type de code, vous pouvez procéder au débogage du processus. Vous pouvez uniquement déboguer les types de code attachés avec succès. Le code non attaché dans le processus sera toujours exécuté, mais vous ne serez pas en mesure de définir des points d’arrêt, afficher des données, ou effectuer d’autres opérations de débogage sur ce code.

 Si vous voulez des informations plus spécifiques sur les raisons pour lesquelles le débbuggeur n’a pas attaché à un type de code, essayez de rattacher à seulement ce type de code.

 **Pour connaître les raisons de l’échec de l’attachement d’un type de code :**

1. Procédez au détachement du processus. Sur le menu **Debug,** sélectionnez **Detach All**.

1. Rattacher au processus, en sélectionnant uniquement le type de code qui n’a pas réussi à se joindre.

    1. Dans la boîte de dialogue **Attacher au processus**, sélectionnez le processus dans la liste **Processus disponibles**.

    2. Sélectionnez **Sélectionner**.

    3. Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes** et le type de code qui a échoué lors de l’attachement. Désélectionner les autres types de code.

    4. Sélectionnez **OK**.

    5. Dans la boîte de dialogue **Attach to Process,** **sélectionnez Attach**.

    Cette fois-ci, l’attachement échoue entièrement et un message d’erreur spécifique s’affiche.

## <a name="see-also"></a>Voir aussi

- [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)
- [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Débogage à distance](../debugger/remote-debugging.md)
