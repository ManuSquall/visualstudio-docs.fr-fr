---
title: Déboguer à distance un projet C++ | Microsoft Docs
description: Découvrez comment déboguer une application Visual Studio C++ à partir d’un ordinateur distant en suivant ces instructions pas à pas.
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: d7723a87471b8f76b9496fe8e7b01e56d1440ee2
ms.sourcegitcommit: 15109ead7991f52092502518a6f4d9061cc22cd2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2021
ms.locfileid: "100335259"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Débogage à distance d’un projet C++ dans Visual Studio
Pour déboguer une application Visual Studio sur un autre ordinateur, installez et exécutez les outils de contrôle à distance sur l’ordinateur sur lequel vous allez déployer votre application, configurez votre projet pour qu’il se connecte à l’ordinateur distant à partir de Visual Studio, puis déployez et exécutez votre application.

![Composants du débogueur distant](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Pour plus d’informations sur le débogage à distance des applications Windows universelles (UWP), consultez [Déboguer un package d’application installé](debug-installed-app-package.md).

## <a name="requirements"></a>Configuration requise

Le débogueur distant est pris en charge sur Windows 7 et versions ultérieures (pas de téléphone) et les versions de Windows Server à partir de Windows Server 2008 Service Pack 2. Pour obtenir la liste complète des conditions requises, consultez [Configuration requise](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Le débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Le débogage sur une connexion à latence élevée ou à faible bande passante, tel qu’Internet à distance ou sur Internet dans les différents pays, n’est pas recommandé et peut échouer ou être trop lent.

## <a name="download-and-install-the-remote-tools"></a>Télécharger et installer les outils de contrôle à distance

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Dans certains scénarios, il peut être plus efficace d’exécuter le débogueur distant à partir d’un partage de fichiers. Pour plus d’informations, consultez [exécuter le débogueur distant à partir d’un partage de fichiers](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Configurer le débogueur distant

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous devez ajouter des autorisations pour des utilisateurs supplémentaires, modifier le mode d’authentification ou le numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> Déboguer à distance un projet C++
 Dans la procédure suivante, le nom et le chemin d’accès du projet sont C:\remotetemp\MyMfc, et le nom de l’ordinateur distant est **MJO-DL**.

1. Créez une application MFC nommée **mymfc**.

2. Définissez un point d’arrêt facilement accessible quelque part dans l’application, par exemple dans **MainFrm.cpp**, au début de `CMainFrame::OnCreate`.

3. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**. Ouvrez l’onglet **Débogage**.

4. Définissez **Débogueur à lancer** sur **Débogueur Windows distant**.

    ![Capture d’écran de l’onglet débogage dans les propriétés de Explorateur de solutions Visual Studio. La propriété débogueur à lancer est définie sur débogueur Windows distant.](../debugger/media/remotedebuggingcplus.png)

5. Appliquez les modifications suivantes aux propriétés :

   |Paramètre|Valeur|
   |-|-|
   |Commande distante|C:\remotetemp\mymfc.exe|
   |Répertoire de travail|C:\remotetemp|
   |Nom du serveur distant|MJO-DL :*numéro_port*|
   |Connexion|À distance avec authentification Windows|
   |Type de débogueur|Natif uniquement|
   |Répertoire de déploiement|C:\remotetemp.|
   |Fichiers supplémentaires à déployer|C:\data\mymfcdata.txt.|

    Si vous déployez des fichiers supplémentaires (facultatif), le dossier doit exister sur les deux ordinateurs.

6. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution et choisissez **Configuration Manager**.

7. Pour la configuration **Debug**, cochez la case **Déployer**.

    ![Capture d’écran de l’Configuration Manager dans le Explorateur de solutions Visual Studio. La configuration Debug est sélectionnée et le déploiement est activé.](../debugger/media/remotedebugcplusdeploy.png)

8. Démarrez le débogage (**Déboguer > Démarrer le débogage** ou appuyez sur **F5**).

9. Le fichier exécutable est déployé automatiquement sur l’ordinateur distant.

10. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à la machine distante.

     Les informations d’identification requises sont spécifiques à la configuration de la sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pouvez choisir un certificat de sécurité ou entrer votre nom de domaine et votre mot de passe. Sur un ordinateur qui n’est pas un domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong> , ainsi que le mot de passe correct.

11. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.

    > [!TIP]
    > Le déploiement des fichiers peut également faire l’objet d’une autre étape. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **mymfc**, puis choisissez **Déployer**.

    Si vous avez des fichiers non-code requis par l’application, vous pouvez les spécifier dans une liste délimitée par des points-virgules dans **fichiers supplémentaires à déployer** sur la page du **débogueur Windows distant** .

    Vous pouvez également inclure les fichiers de votre projet et définir la propriété de **contenu** sur **Oui** dans la page **Propriétés** de chaque fichier. Ces fichiers sont copiés dans le **Répertoire de déploiement** spécifié sur la page du **débogueur Windows distant** . Vous pouvez également modifier le **type d’élément** pour **copier le fichier** et spécifier des propriétés supplémentaires ici si vous avez besoin de copier les fichiers dans un sous-dossier du **Répertoire de déploiement**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Voir aussi
- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Débogage distant ASP.NET sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)