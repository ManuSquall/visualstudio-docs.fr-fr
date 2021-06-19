---
title: Attacher aux processus en cours d’exécution avec le débogueur
description: Découvrez comment attacher le débogueur Visual Studio à un processus en cours d’exécution sur un ordinateur local ou distant.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e3836403af80d06a2ecaa7f77cb7f49f0c6f0e8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389785"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Attacher aux processus en cours d’exécution avec le débogueur Visual Studio

Vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution sur un ordinateur local ou distant. Une fois le processus en cours d’exécution, sélectionnez **Déboguer**  >  **attacher au processus** ou appuyez sur **CTRL** + **ALT** + **p** dans Visual Studio, puis utilisez la boîte de dialogue **attacher au processus** pour attacher le débogueur au processus.

Vous pouvez utiliser **attacher au processus** pour déboguer des applications en cours d’exécution sur des ordinateurs locaux ou distants, déboguer plusieurs processus simultanément, déboguer des applications qui n’ont pas été créées dans Visual Studio, ou déboguer une application que vous n’avez pas démarrée à partir de Visual Studio avec le débogueur attaché. Par exemple, si vous exécutez une application sans le débogueur et que vous n’avez pas atteint une exception, vous pouvez attacher le débogueur au processus qui exécute l’application et commencer le débogage.

> [!TIP]
> Vous ne savez pas s’il faut utiliser l' **attachement au processus** pour votre scénario de débogage ? Consultez [scénarios de débogage courants](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Attacher à un processus en cours d’exécution sur votre ordinateur local

Pour vous rattacher rapidement à un processus que vous avez attaché précédemment, consultez [rattacher à un processus](#BKMK_reattach).

**Pour attacher un processus sur votre ordinateur local :**

1. Dans Visual Studio, sélectionnez **Déboguer**  >  **attacher au processus** (ou appuyez sur **CTRL** + **ALT** + **P**) pour ouvrir la boîte de dialogue **attacher au processus** .

1. Vérifiez le **type de connexion**.

   Dans la plupart des scénarios, vous pouvez utiliser la **valeur par défaut**. Certains scénarios peuvent nécessiter un type de connexion différent. Pour plus d’informations, consultez les autres sections de cet article ou [scénarios de débogage courants](#BKMK_Scenarios).

1. Définissez la **cible** de la connexion sur le nom de votre ordinateur local.

   ![Capture d’écran de la boîte de dialogue Attacher au processus, avec la cible de connexion définie sur le nom de l’ordinateur local.](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. Dans la liste **processus disponibles** , recherchez et sélectionnez le ou les processus que vous voulez attacher.

   - Pour sélectionner rapidement un processus, tapez son nom ou sa première lettre dans la zone **Filtrer les processus** .

   - Si vous ne connaissez pas le nom du processus, parcourez la liste ou consultez les [scénarios de débogage courants](#BKMK_Scenarios) pour certains noms de processus courants.

   >[!TIP]
   >Les processus peuvent démarrer et s’arrêter en arrière-plan pendant que la boîte de dialogue **attacher au processus** est ouverte, de sorte que la liste des processus en cours d’exécution ne soit pas toujours à jour. Vous pouvez sélectionner **Actualiser** à tout moment pour afficher la liste actuelle.

1. Dans le champ **attacher à** , assurez-vous que le type de code que vous envisagez de déboguer est listé. Le paramètre **automatique** par défaut fonctionne pour la plupart des types d’applications.

   Si vous utilisez le type de connexion **par défaut** , vous pouvez sélectionner manuellement le type de code que vous voulez attacher. Dans le cas contraire, l’option **Select** peut être désactivée.

   Pour sélectionner les types de code manuellement :
   1. Cliquez sur **Sélectionner**.
   1. Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes**.
      Si vous rencontrez un problème lors de l’attachement à un processus de la liste, vous pouvez utiliser la boîte de dialogue [Sélectionner le type de code](../debugger/select-code-type-dialog-box.md) pour vous aider à [résoudre](#BKMK_Troubleshoot_attach_errors) le problème.
   1. Sélectionnez les types de code que vous souhaitez déboguer.
   1. Sélectionnez **OK**.

1. Sélectionnez **Attacher**.

>[!NOTE]
>Vous pouvez être attaché à plusieurs applications pour le débogage, mais une seule application est active dans le débogueur à la fois. Vous pouvez définir l’application active dans la barre d’outils d' **emplacement de débogage** de Visual Studio ou dans la fenêtre **processus** .

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Attacher à un processus sur un ordinateur distant

Vous pouvez également sélectionner un ordinateur distant dans la boîte de dialogue **attacher au processus** , afficher une liste des processus disponibles exécutés sur cet ordinateur et les attacher à un ou plusieurs processus de débogage. Le débogueur distant (*msvsmon.exe*) doit être en cours d’exécution sur l’ordinateur distant. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).

Pour obtenir des instructions plus complètes sur le débogage des applications ASP.NET qui ont été déployées sur IIS, consultez [débogage distant ASP.net sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Pour attacher un processus en cours d’exécution sur un ordinateur distant :**

1. Dans Visual Studio, sélectionnez **Déboguer**  >  **attacher au processus** (ou appuyez sur **CTRL** + **ALT** + **P**) pour ouvrir la boîte de dialogue **attacher au processus** .

1. Vérifiez le **type de connexion**.

   Dans la plupart des scénarios, vous pouvez utiliser la **valeur par défaut**. Certains scénarios, tels que le débogage de Linux ou une application en conteneur, requièrent un type de connexion différent. Pour plus d’informations, consultez les autres sections de cet article ou [scénarios de débogage courants](#BKMK_Scenarios).

1. Dans la zone cible de la **connexion** , sélectionnez l’ordinateur distant, en utilisant l’une des méthodes suivantes :

   - Sélectionnez la flèche déroulante cible de la **connexion**, puis sélectionnez le nom de l’ordinateur dans la liste déroulante.
   - Tapez le nom de l’ordinateur dans la zone cible de la **connexion** , puis appuyez sur **entrée**.

     Vérifiez que Visual Studio ajoute le port requis au nom de l’ordinateur, qui apparaît au format suivant : **\<remote computer name> :p Trier**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Si vous ne pouvez pas vous connecter à l’aide du nom de l’ordinateur distant, essayez d’utiliser l’adresse IP et l’adresse du port (par exemple, `123.45.678.9:4022` ). 4024 est le port par défaut pour le débogueur distant Visual Studio 2019 x64. Pour d’autres affectations de port du débogueur distant, consultez [affectations de port du débogueur distant](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Si vous ne pouvez pas vous connecter à l’aide du nom de l’ordinateur distant, essayez d’utiliser l’adresse IP et l’adresse du port (par exemple, `123.45.678.9:4022` ). 4022 est le port par défaut pour le débogueur distant Visual Studio 2017 x64. Pour d’autres affectations de port du débogueur distant, consultez [affectations de port du débogueur distant](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Sélectionnez le bouton **Rechercher** en regard de la zone **cible** de la connexion pour ouvrir la boîte de dialogue **connexions à distance** . La boîte de dialogue **connexions à distance** répertorie tous les périphériques qui se trouvent sur votre sous-réseau local ou directement connectés à votre ordinateur. Vous devrez peut-être [ouvrir le port UDP 3702](../debugger/remote-debugger-port-assignments.md) sur le serveur pour détecter les périphériques distants. Sélectionnez l’ordinateur ou le périphérique souhaité, puis cliquez sur **Sélectionner**.

   > [!NOTE]
   > Le paramètre de **type de connexion** persiste entre les sessions de débogage. Le paramètre de **cible de connexion** persiste entre les sessions de débogage uniquement si une connexion de débogage réussie a eu lieu avec cette cible.

3. Cliquez sur **Actualiser** pour remplir la liste des **processus disponibles** .

    >[!TIP]
    >Les processus peuvent démarrer et s’arrêter en arrière-plan pendant que la boîte de dialogue **attacher au processus** est ouverte, de sorte que la liste des processus en cours d’exécution ne soit pas toujours à jour. Vous pouvez sélectionner **Actualiser** à tout moment pour afficher la liste actuelle.

4. Dans la liste **processus disponibles** , recherchez et sélectionnez le ou les processus que vous voulez attacher.

   - Pour sélectionner rapidement un processus, tapez son nom ou sa première lettre dans la zone **Filtrer les processus** .

   - Si vous ne connaissez pas le nom du processus, parcourez la liste ou consultez les [scénarios de débogage courants](#BKMK_Scenarios) pour certains noms de processus courants.

   - Pour rechercher les processus s’exécutant sous tous les comptes d’utilisateur, activez la case à cocher **afficher les processus de tous les utilisateurs** .

     >[!NOTE]
     >Si vous essayez d’établir un attachement à un processus appartenant à un compte d’utilisateur non fiable, une boîte de dialogue d’avertissement de sécurité s’affiche avec un message de confirmation. Pour plus d’informations [, consultez Avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou si vous n’êtes pas sûr, n’effectuez pas l’attachement à ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. Dans le champ **attacher à** , assurez-vous que le type de code que vous envisagez de déboguer est listé. Le paramètre **automatique** par défaut fonctionne pour la plupart des types d’applications.

   Si vous utilisez le type de connexion **par défaut** , vous pouvez sélectionner manuellement le type de code que vous voulez attacher. Dans le cas contraire, l’option **Select** peut être désactivée.

   Pour sélectionner les types de code manuellement :
   1. Cliquez sur **Sélectionner**.
   1. Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes**.
      Si vous rencontrez un problème lors de l’attachement à un processus de la liste, vous pouvez utiliser la boîte de dialogue [Sélectionner le type de code](../debugger/select-code-type-dialog-box.md) pour vous aider à [résoudre](#BKMK_Troubleshoot_attach_errors) le problème.
   1. Sélectionnez **OK**.

6. Sélectionnez **Attacher**.

>[!NOTE]
>Vous pouvez être attaché à plusieurs applications pour le débogage, mais une seule application est active dans le débogueur à la fois. Vous pouvez définir l’application active dans la barre d’outils d' **emplacement de débogage** de Visual Studio ou dans la fenêtre **processus** .

Dans certains cas, lorsque vous déboguez dans une session Bureau à distance (services Terminal Server), la liste **processus disponibles** n’affiche pas tous les processus disponibles. Si vous exécutez Visual Studio en tant qu’utilisateur disposant d’un compte d’utilisateur limité, la liste **processus disponibles** n’affiche pas les processus qui s’exécutent dans la session 0. La session 0 est utilisée pour les services et autres processus serveur, y compris *w3wp.exe*. Vous pouvez résoudre le problème en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous un compte administrateur ou en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la console du serveur au lieu d’une session Terminal Server.

Si aucune de ces solutions n’est possible, la troisième option consiste à attacher le débogueur au processus en exécutant `vsjitdebugger.exe -p <ProcessId>` à partir de la ligne de commande Windows. Vous pouvez déterminer l’ID de processus à l’aide de *tlist.exe*. Pour obtenir *tlist.exe*, téléchargez et installez les outils de débogage pour Windows, qui sont disponibles dans [Téléchargements relatifs au WDK et à WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Attachement à un processus .NET Core s’exécutant sur Linux à l’aide de SSH

Pour plus d’informations, consultez [Déboguer à distance .net Core s’exécutant sur Linux à l’aide de SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Attacher à un processus en cours d’exécution sur un conteneur d’ancrage

À compter de Visual Studio 2019, vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution sur un conteneur d’ancrage. Pour obtenir un conteneur d’ancrage Linux .NET Core, consultez [attacher à un processus en cours d’exécution sur un conteneur d’ancrage Linux](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container). Pour obtenir un conteneur Windows Dockr, consultez [attacher à un processus en cours d’exécution sur un conteneur Windows dockr](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container).

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Rattacher à un processus

Vous pouvez rattacher rapidement les processus auxquels vous étiez précédemment attaché en choisissant **Déboguer**  >  **rattacher au processus** (**MAJ** + **ALT** + **P**). Quand vous choisissez cette commande, le débogueur tente immédiatement d’attacher les derniers processus que vous avez attachés en tentant d’abord de faire correspondre l’ID de processus précédent et, en cas d’échec, en faisant correspondre le nom du processus précédent. Si aucune correspondance n’est trouvée, ou si plusieurs processus portent le même nom, la boîte **de dialogue Attacher au processus** s’ouvre et vous permet de sélectionner le processus approprié.

> [!NOTE]
> La commande **rattacher au processus** est disponible à partir de Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Scénarios de débogage courants

Pour vous aider à déterminer s’il faut utiliser l' **attachement au processus** et le processus à attacher, le tableau suivant présente quelques scénarios de débogage courants, avec des liens vers des instructions supplémentaires disponibles. (La liste n’est pas exhaustive.)

Pour certains types d’applications, comme les applications Windows universelles (UWP), vous n’êtes pas directement attaché à un nom de processus, mais utilisez plutôt l’option de menu **déboguer le package d’application installé** dans Visual Studio (consultez le tableau).

Pour que le débogueur s’attache au code écrit en C++, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Pour le débogage de scripts côté client, le débogage de script doit être activé dans le navigateur. Pour déboguer le script côté client sur chrome, choisissez **JavaScript (chrome)** ou **JavaScript (Microsoft Edge-chrome)** comme type de code et, en fonction de votre type d’application, vous devrez peut-être fermer toutes les instances de chrome et démarrer le navigateur en mode débogage (type `chrome.exe --remote-debugging-port=9222` à partir d’une ligne de commande). Dans les versions antérieures de Visual Studio, le débogueur de script pour Chrome était le **Kit Web**.

Pour sélectionner rapidement un processus en cours d’exécution à attacher, dans Visual Studio, tapez **CTRL** + **ALT** + **P**, puis tapez la première lettre du nom de processus.

|Scénario|Méthode de débogage|Nom du processus|Notes et liens|
|-|-|-|-|
|Débogage à distance ASP.NET 4 ou 4,5 sur un serveur IIS|Utiliser les outils de contrôle à distance et **attacher au processus**|*w3wp.exe*|Voir [débogage à distance ASP.net sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Débogage à distance ASP.NET Core sur un serveur IIS|Utiliser les outils de contrôle à distance et **attacher au processus**|*w3wp.exe* ou *dotnet.exe*|À compter de .NET Core 3, le processus de *w3wp.exe* est utilisé pour le [modèle d’hébergement dans l’application](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models)par défaut. Pour le déploiement d’applications, consultez [publier sur IIS](/aspnet/core/host-and-deploy/iis/). Pour plus d’informations, consultez [ASP.net Core du débogage distant sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach) .|
|Déboguer le script côté client sur un serveur IIS local, pour les types d’applications pris en charge |Utiliser l' **attachement au processus**|*chrome.exe*, *MicrosoftEdgeCP.exe* ou *iexplore.exe*|Le débogage de script doit être activé. Pour Chrome, vous devez également exécuter chrome en mode débogage ( `chrome.exe --remote-debugging-port=9222` de type à partir d’une ligne de commande) et sélectionner **JavaScript (chrome)** dans le champ **attacher à** .|
|Déboguer une application C#, Visual Basic ou C++ sur l’ordinateur local|Utiliser le débogage standard (**F5**) ou l' **attachement au processus**|*\<appname>.exe*|Dans la plupart des scénarios, utilisez le débogage standard et non l' **attachement au processus**.|
|Débogage à distance d’une application de bureau Windows|outils de contrôle à distance.|N/A| Voir [Déboguer à distance une application C# ou Visual Basic](../debugger/remote-debugging-csharp.md) , ou [Déboguer à distance une application C++](../debugger/remote-debugging-cpp.md)|
|Déboguer .NET Core sur Linux|Utiliser l' **attachement au processus**|*dotnet.exe* ou un nom de processus unique|Pour utiliser SSH, consultez [Déboguer à distance .net Core s’exécutant sur Linux à l’aide de SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Pour les applications en conteneur, consultez [attacher à un processus en cours d’exécution dans un conteneur d’ancrage](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container).|
|Déboguer une application en conteneur|Utiliser l' **attachement au processus**|*dotnet.exe* ou un nom de processus unique|Consultez [attacher à un processus en cours d’exécution dans un conteneur d’ancrage](../debugger/attach-to-process-running-in-docker-container.md)|
|Déboguer à distance Python sur Linux|Utiliser l' **attachement au processus**|*debugpy*|Voir [attachement à distance à partir des outils python](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Déboguer une application ASP.NET sur l’ordinateur local après avoir démarré l’application sans le débogueur|Utiliser l' **attachement au processus**|*iiexpress.exe*|Cela peut être utile pour accélérer le chargement de votre application, par exemple lors du profilage. |
|Déboguer d’autres types d’applications pris en charge sur un processus serveur|Si le serveur est distant, utilisez les outils de contrôle à distance et **Attachez-le au processus**|*chrome.exe*, *iexplore.exe* ou autres processus|Si nécessaire, utilisez moniteur de ressource pour aider à identifier le processus. Consultez [Débogage à distance](../debugger/remote-debugging.md).|
|Déboguer à distance une application Windows universelle (UWP), OneCore, HoloLens ou une application IoT|Déboguer un package d’application installé|N/A|Consultez [Déboguer un package d’application installé](debug-installed-app-package.md) au lieu d’utiliser l' **attachement au processus**|
|Déboguer une application Windows universelle (UWP), OneCore, HoloLens ou IoT que vous n’avez pas démarrée à partir de Visual Studio|Déboguer un package d’application installé|N/A|Consultez [Déboguer un package d’application installé](debug-installed-app-package.md) au lieu d’utiliser l' **attachement au processus**|

## <a name="use-debugger-features"></a>Utiliser les fonctionnalités du débogueur

Pour utiliser les fonctionnalités complètes du débogueur Visual Studio (comme l’atteinte des points d’arrêt) lors de l’attachement à un processus, l’application doit correspondre exactement à la source et aux symboles locaux. Autrement dit, le débogueur doit être en mesure de charger les [fichiers de symboles (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)corrects. Par défaut, cela nécessite une version Debug.

Pour les scénarios de débogage distant, vous devez disposer du code source (ou d’une copie du code source) déjà ouvert dans Visual Studio. Les fichiers binaires de l’application compilée sur l’ordinateur distant doivent provenir de la même build que sur l’ordinateur local.

Dans certains scénarios de débogage local, vous pouvez déboguer dans Visual Studio sans avoir accès à la source si les fichiers de symboles appropriés sont présents avec l’application. Par défaut, cela nécessite une version Debug. Pour plus d’informations, consultez [spécifier des fichiers de symboles et sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Résoudre les erreurs d’attachement

Dans certains scénarios, le débogueur peut avoir besoin d’aide pour identifier correctement le type de code à déboguer. Si les valeurs de connexion sont correctement définies (vous pouvez afficher le processus approprié dans la liste **processus disponibles** ), mais que le débogueur ne parvient pas à s’attacher, essayez de sélectionner le type de connexion le plus approprié dans la liste **type de connexion** , ce qui peut être nécessaire, par exemple, si vous déboguez une application Linux ou python. Si vous utilisez le type de connexion par défaut, vous pouvez également sélectionner le type de code spécifique auquel se connecter, comme décrit plus loin dans cette section.

Quand le débogueur est attaché à un processus en cours d’exécution, le processus peut contenir un ou plusieurs types de code. Les types de code auxquels le débogueur peut s’attacher sont affichés et sélectionnés dans la boîte de dialogue [Sélectionner le type de code](../debugger/select-code-type-dialog-box.md) .

Parfois, le débogueur peut réussir à s’attacher à un type de code, mais pas aux autres. En général, cela se produit dans les cas suivants :

- Vous essayez de vous attacher à un processus qui s’exécute sur un ordinateur distant. Il est possible que des composants de débogage distant soient installés pour certains types de code, mais pas pour d’autres, sur l’ordinateur distant.
- Vous essayez de vous attacher à deux ou plusieurs processus pour le débogage de base de données direct. Le débogage SQL prend en charge l’attachement à un seul processus uniquement.

Si le débogueur peut être attaché à certains des types de code, mais pas à tous, un message identifie les types qui n’ont pas pu être attachés.

Si le débogueur parvient à s’attacher à au moins un type de code, vous pouvez procéder au débogage du processus. Vous pouvez uniquement déboguer les types de code attachés avec succès. Le code non attaché dans le processus s’exécute toujours, mais vous ne pouvez pas définir de points d’arrêt, afficher des données ou effectuer d’autres opérations de débogage sur ce code.

Si vous souhaitez des informations plus spécifiques sur la raison pour laquelle le débogueur n’a pas réussi à s’attacher à un type de code, essayez de rattacher uniquement ce type de code.

**Pour connaître les raisons de l’échec de l’attachement d’un type de code :**

1. Procédez au détachement du processus. Dans le menu **Déboguer** , sélectionnez **détacher tout**.

1. Rattachez le processus en sélectionnant uniquement le type de code qui n’a pas réussi à s’attacher.

    1. Dans la boîte de dialogue **Attacher au processus**, sélectionnez le processus dans la liste **Processus disponibles**.

    2. Sélectionnez **Sélectionner**.

    3. Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes** et le type de code qui a échoué lors de l’attachement. Désélectionnez les autres types de code.

    4. Sélectionnez **OK**.

    5. Dans la boîte de dialogue **attacher au processus** , sélectionnez **attacher**.

    Cette fois-ci, l’attachement échoue entièrement et un message d’erreur spécifique s’affiche.

## <a name="see-also"></a>Voir aussi

- [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)
- [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Débogage distant](../debugger/remote-debugging.md)
