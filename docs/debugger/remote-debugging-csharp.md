---
title: Débogage à distance un C# ou projet Visual Basic | Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 82873b29a173209739497087a4dfe5b293123e2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055658"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Débogage à distance un C# ou un projet Visual Basic dans Visual Studio
Pour déboguer une application de Visual Studio qui a été déployée sur un autre ordinateur, installer et exécuter les outils à distance sur l’ordinateur où vous avez déployé votre application, configurez votre projet pour se connecter à l’ordinateur distant à partir de Visual Studio, puis exécutez votre application.

![Composants du débogueur distant](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Pour plus d’informations sur le débogage des applications de Windows universelle (UWP) à distance, consultez [déboguer un Package d’application installé](debug-installed-app-package.md).

## <a name="requirements"></a>Spécifications

Le débogueur distant est pris en charge sur Windows 7 et versions ultérieures (pas de téléphone) et les versions de Windows Server depuis Windows Server 2008 Service Pack 2. Pour obtenir une liste complète des exigences, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou faible bande passante, telles que la numérotation Internet, ou via Internet entre les pays n’est pas recommandé et peut échouer ou être trop faibles.
  
## <a name="download-and-install-the-remote-tools"></a>Télécharger et installer les outils de contrôle à distance

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Dans certains scénarios, il peut être plus efficace d’exécuter le débogueur distant à partir d’un partage de fichiers. Pour plus d’informations, consultez [exécuter le débogueur distant à partir d’un partage de fichiers](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurer le débogueur distant

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous avez besoin pour ajouter des autorisations pour les utilisateurs supplémentaires, modifiez le mode d’authentification, ou le numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> Le projet de débogage à distance
Le débogueur ne peut pas déployer d’applications de bureau Visual C# ou Visual Basic sur un ordinateur distant, mais vous pouvez toujours les déboguer à distance comme suit. La procédure suivante suppose que vous souhaitez déboguer sur un ordinateur nommé **MJO-DL**, comme illustré dans l’illustration ci-dessous.
  
1. Créez un projet WPF nommé **MyWpf**.  
  
2. Définissez un point d’arrêt facilement accessible quelque part dans le code.  
  
    Par exemple, vous pouvez définir un point d’arrêt dans un gestionnaire de boutons. Pour ce faire, ouvrez MainWindow.xaml et ajouter un contrôle de bouton à partir de la boîte à outils, puis double-cliquez sur le bouton pour ouvrir son gestionnaire.
  
3. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **propriétés**.  
  
4. Dans la page **Propriétés**, choisissez l’onglet **Déboguer**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Assurez-vous que la zone de texte **Répertoire de travail** est vide.  
  
6. Choisissez **utiliser l’ordinateur distant**et le type **MJO-DL:4022** dans la zone de texte. (4022 est le numéro de port indiqué dans la fenêtre du débogueur distant. Le numéro de port incrémente 2 dans chaque version de Visual Studio).
  
7. Vérifiez que l’option **Permettre le débogage du code natif** n’est pas sélectionnée.  
  
8. Générez le projet.  
  
9. Créez un dossier sur l’ordinateur distant ayant le même chemin que le dossier **Debug** sur votre ordinateur Visual Studio : **\<<chemin_source>\MyWPF\MyWPF\bin\Debug**.  
  
10. Copiez le fichier exécutable que vous venez de créer à partir de votre ordinateur Visual Studio dans le dossier nouvellement créé sur l’ordinateur distant.
  
    > [!CAUTION]
    >  Ne pas modifier le code ou la reconstruction (ou vous devez répéter cette étape). Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.

    Vous pouvez copier le projet manuellement, utilisez Xcopy, Robocopy, Powershell ou autres options.
  
11. Assurez-vous que le débogueur distant est en cours d’exécution sur l’ordinateur cible (si elle n’est pas le cas, recherchez **débogueur distant** dans le **Démarrer** menu). Voici à quoi ressemble la fenêtre du débogueur distant.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Dans Visual Studio, démarrez le débogage (**Déboguer > Démarrer le débogage** ou appuyez sur **F5**).  
  
13. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à l’ordinateur distant.  
  
     Les informations d’identification requises varient selon la configuration de la sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez entrer votre nom de domaine et le mot de passe. Sur un ordinateur n’appartenant pas au domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong>, ainsi que le mot de passe correct.

     La fenêtre principale de l’application WPF doit être ouverte sur l’ordinateur distant.
  
14. Si nécessaire, prendre des mesures pour atteindre le point d’arrêt. Il doit être actif. Si elle n’est pas le cas, les symboles pour l’application n’est pas chargé. Nouvelle tentative et si cela ne fonctionne pas, obtenir des informations sur le chargement de symboles et comment les résoudre à [paramètres des symboles de présentation des fichiers de symboles et de Visual Studio](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.
  
    Si vous avez des fichiers de code non qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires (dans l’**Explorateur de solutions**, cliquez sur **Ajouter > Nouveau dossier**). Ensuite, ajoutez les fichiers au dossier (dans l’**Explorateur de solutions**, cliquez sur **Ajouter > Élément existant**, puis sélectionnez les fichiers). Dans la page **Propriétés** de chaque fichier, définissez **Copier dans le répertoire de sortie** sur **Toujours copier**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)   
 [Configurer le Pare-feu Windows pour le débogage à distance](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)