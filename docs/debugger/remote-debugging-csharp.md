---
title: Remote Debug un projet C ou VB Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302097"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Remote Debugging un projet de base visuelle ou de Cmd dans Visual Studio
Pour déboguer une application Visual Studio qui a été déployée sur un ordinateur différent, installez et exécutez les outils distants de l’ordinateur où vous avez déployé votre application, configurez votre projet pour vous connecter à l’ordinateur distant de Visual Studio, puis exécutez votre application.

![Composants de débbuggeurs à distance](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Pour plus d’informations sur les applications Windows Universelles (UWP) à distance, voir [Debug an Installed App Package](debug-installed-app-package.md).

## <a name="requirements"></a>Spécifications

Le débbugger à distance est pris en charge sur Windows 7 et plus récent (pas téléphone) et les versions de Windows Server à partir de Windows Server 2008 Service Pack 2. Pour une liste complète des exigences, voir [Exigences](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Le débogage entre deux ordinateurs connectés par un proxy n’est pas pris en charge. Il n’est pas recommandé de déracyer une latence élevée ou une faible connexion à bande passante, comme Internet commutée ou sur Internet à travers les pays, et peut échouer ou être inacceptablement lent.

## <a name="download-and-install-the-remote-tools"></a>Télécharger et installer les outils de contrôle à distance

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Dans certains scénarios, il peut être plus efficace d’exécuter le débbuggeur à distance à partir d’une part de fichier. Pour plus d’informations, voir [Exécuter le débbugger à distance à partir d’une part de fichier](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Configurer le débbugger à distance

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous avez besoin d’ajouter des autorisations pour d’autres utilisateurs, modifier le mode d’authentification, ou le numéro de port pour le débbugger à distance, voir [Configure Configurer le débbugger à distance](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Débogé à distance du projet
Le débogueur ne peut pas déployer d’applications de bureau Visual C# ou Visual Basic sur un ordinateur distant, mais vous pouvez toujours les déboguer à distance comme suit. La procédure suivante suppose que vous voulez le déboblir sur un ordinateur nommé **MJO-DL**, comme indiqué dans l’illustration ci-dessous.

1. Créez un projet WPF nommé **MyWpf**.

2. Définissez un point d’arrêt facilement accessible quelque part dans le code.

    Par exemple, vous pouvez définir un point d’arrêt dans un gestionnaire de boutons. Pour ce faire, ouvrez MainWindow.xaml, et ajoutez un contrôle bouton de la boîte à outils, puis double-cliquez sur le bouton pour ouvrir son gestionnaire.

3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Propriétés**.

4. Dans la page **Propriétés**, choisissez l’onglet **Déboguer**.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Assurez-vous que la zone de texte **Répertoire de travail** est vide.

6. Choisissez **Utilisez la machine à distance,** et **tapez yourmachinename: port** dans la boîte de texte. (Le numéro de port est indiqué dans la fenêtre de débâgneur à distance. Le numéro de port incréments 2 dans chaque version de Visual Studio).

    Dans cet exemple, utilisez :
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** sur Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** sur Visual Studio 2017
    ::: moniker-end

7. Vérifiez que l’option **Permettre le débogage du code natif** n’est pas sélectionnée.

8. Créez le projet.

9. Créez un dossier sur l’ordinateur distant ayant le même chemin que le dossier **Debug** sur votre ordinateur Visual Studio : **\<<chemin_source>\MyWPF\MyWPF\bin\Debug**.

10. Copiez le fichier exécutable que vous venez de créer à partir de votre ordinateur Visual Studio dans le dossier nouvellement créé sur l’ordinateur distant.

    > [!CAUTION]
    > N’effectuez pas de modifications au code ou ne reconstruisez pas (ou vous devez répéter cette étape). Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.

    Vous pouvez copier le projet manuellement, utiliser Xcopy, Robocopy, Powershell, ou d’autres options.

11. Assurez-vous que le débbuggeur à distance est en cours d’exécution sur la machine cible (Si ce n’est pas le cas, recherchez **Remote Debugger** dans le menu **Démarrer).** La fenêtre de débogénaire à distance ressemble à ceci.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. Dans Visual Studio, démarrez le débogage (**Déboguer > Démarrer le débogage** ou appuyez sur **F5**).

13. En cas d’ensemanie, saisissez les informations d’identification du réseau pour vous connecter à la machine distante.

     Les informations d’identification requises varient en fonction de la configuration de sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez entrer votre nom de domaine et mot de passe. Sur une machine non-domaine, vous pouvez entrer le nom <strong>MJO-DL\name@something.com</strong>de la machine et un nom de compte d’utilisateur valide, comme , avec le mot de passe correct.

     La fenêtre principale de l’application WPF doit être ouverte sur l’ordinateur distant.

14. Si nécessaire, prenez des mesures pour atteindre le point d’arrêt. Il doit être actif. Sinon, cela signifie que les symboles de l’application n’ont pas été chargés. Retry, et si cela ne fonctionne pas, obtenir des informations sur le chargement des symboles et comment les dépanner à [Comprendre les fichiers symbole et les paramètres de symbole Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.

    Si vous avez des fichiers non codés qui doivent être utilisés par l’application, vous devez les inclure dans le projet Visual Studio. Créez un dossier de projet pour les fichiers supplémentaires (dans la **Solution Explorer**, cliquez sur Ajouter > **nouveau dossier**). Ensuite, ajoutez les fichiers au dossier (dans l’**Explorateur de solutions**, cliquez sur **Ajouter > Élément existant**, puis sélectionnez les fichiers). Dans la page **Propriétés** de chaque fichier, définissez **Copier dans le répertoire de sortie** sur **Toujours copier**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Voir aussi
- [Débogage dans Visual Studio](../debugger/index.yml)
- [Premier regard sur le débbugger](../debugger/debugger-feature-tour.md)
- [Configurer le pare-feu Windows pour le débugging à distance](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)