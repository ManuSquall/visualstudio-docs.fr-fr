---
title: Remote Debug a C ' Microsoft Docs
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302111"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Remote Debugging un projet CMD dans Visual Studio
Pour déboguer une application Visual Studio sur un ordinateur différent, installez et exécutez les outils distants de l’ordinateur où vous déployez votre application, configurez votre projet pour vous connecter à l’ordinateur distant de Visual Studio, puis déployez et exécuterez votre application.

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

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Débogé à distance d’un projet de C
 Dans la procédure suivante, le nom et le chemin du projet est C: 'remotetemp’MyMfc, et le nom de l’ordinateur distant est **MJO-DL**.

1. Créez une application MFC nommée **mymfc**.

2. Définissez un point d’arrêt facilement accessible quelque part dans l’application, par exemple dans **MainFrm.cpp**, au début de `CMainFrame::OnCreate`.

3. Dans Solution Explorer, cliquez à droite sur le projet et sélectionnez **propriétés**. Ouvrez l’onglet **Débogage**.

4. Définissez **Débogueur à lancer** sur **Débogueur Windows distant**.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Appliquez les modifications suivantes aux propriétés :

   |Paramètre|Valeur|
   |-|-|
   |Commande distante|C:\remotetemp\mymfc.exe|
   |Répertoire de travail|C:\remotetemp|
   |Nom du serveur distant|MJO-DL:*portnumber*|
   |Connexion|À distance avec authentification Windows|
   |Type de débogueur|Natif uniquement|
   |Répertoire de déploiement|C:\remotetemp.|
   |Fichiers supplémentaires à déployer|C:\data\mymfcdata.txt.|

    Si vous déployez des fichiers supplémentaires (facultatif), le dossier doit exister sur les deux machines.

6. Dans Solution Explorer, cliquez à droite sur la solution et choisissez **Configuration Manager**.

7. Pour la configuration **Debug**, cochez la case **Déployer**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Démarrez le débogage (**Déboguer > Démarrer le débogage** ou appuyez sur **F5**).

9. Le fichier exécutable est déployé automatiquement sur l’ordinateur distant.

10. En cas d’ensemanie, saisissez les informations d’identification du réseau pour vous connecter à la machine distante.

     Les informations d’identification requises sont spécifiques à la configuration de sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez choisir un certificat de sécurité ou entrer votre nom de domaine et mot de passe. Sur une machine non-domaine, vous pouvez entrer le nom <strong>MJO-DL\name@something.com</strong>de la machine et un nom de compte d’utilisateur valide, comme , avec le mot de passe correct.

11. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.

    > [!TIP]
    > Le déploiement des fichiers peut également faire l’objet d’une autre étape. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **mymfc**, puis choisissez **Déployer**.

    Si vous avez des fichiers non codés qui sont requis par l’application, vous pouvez les spécifier dans **des fichiers supplémentaires à déployer** sur la page Remote Windows **Debugger.**

    Alternativement, vous pouvez inclure les fichiers dans votre projet, et définir la propriété **Content** à **Oui** dans la page **Propriétés** pour chaque fichier. Ces fichiers sont copiés sur **l’annuaire de déploiement** spécifié sur la page Remote Windows **Debugger.** Vous pouvez également modifier le **type d’élément** pour **copier le fichier** et spécifier des propriétés supplémentaires si vous avez besoin que les fichiers soient copiés sur un sous-pli de l’annuaire de **déploiement**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Voir aussi
- [Débogage dans Visual Studio](../debugger/index.yml)
- [Premier regard sur le débbugger](../debugger/debugger-feature-tour.md)
- [Configurer le pare-feu Windows pour le débugging à distance](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)