---
title: Un projet Visual C++ de débogage à distance | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
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
ms.openlocfilehash: ca380bae4ae4fcca5f280eb00533ad8ed7763f9e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709289"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Un projet Visual C++ dans Visual Studio de débogage à distance
Pour déboguer une application de Visual Studio sur un autre ordinateur, installer et exécuter les outils à distance sur l’ordinateur où vous allez déployer votre application, configurez votre projet pour vous connecter à l’ordinateur distant à partir de Visual Studio, puis déployer et exécuter votre application.

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

## <a name="remote_cplusplus"></a> Débogage distant d’un projet Visual C++
 Dans la procédure suivante, le nom et le chemin d’accès du projet est C:\remotetemp\MyMfc, et le nom de l’ordinateur distant est **MJO-DL**.

1. Créez une application MFC nommée **mymfc**.

2. Définissez un point d’arrêt facilement accessible quelque part dans l’application, par exemple dans **MainFrm.cpp**, au début de `CMainFrame::OnCreate`.

3. Dans l’Explorateur de solutions, cliquez sur le projet, puis sélectionnez **propriétés**. Ouvrez l’onglet **Débogage**.

4. Définissez **Débogueur à lancer** sur **Débogueur Windows distant**.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Appliquez les modifications suivantes aux propriétés :

   |Paramètre|Value|
   |-|-|
   |Commande distante|C:\remotetemp\mymfc.exe|
   |Répertoire de travail|C:\remotetemp|
   |Nom du serveur distant|DL-MJO :*numéro_port*|
   |Connexion|À distance avec authentification Windows|
   |Type de débogueur|Natif uniquement|
   |Répertoire de déploiement|C:\remotetemp.|
   |Fichiers supplémentaires à déployer|C:\data\mymfcdata.txt.|

    Si vous déployez des fichiers supplémentaires (facultatifs), le dossier doit exister sur les deux ordinateurs.

6. Dans l’Explorateur de solutions, cliquez sur la solution et choisissez **Configuration Manager**.

7. Pour la configuration **Debug**, cochez la case **Déployer**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Démarrez le débogage (**Déboguer > Démarrer le débogage** ou appuyez sur **F5**).

9. Le fichier exécutable est déployé automatiquement sur l’ordinateur distant.

10. Si vous y êtes invité, entrez les informations d’identification réseau pour vous connecter à l’ordinateur distant.

     Les informations d’identification requises sont spécifiques à la configuration de la sécurité de votre réseau. Par exemple, sur un ordinateur de domaine, vous pourrez choisir un certificat de sécurité ou entrez votre nom de domaine et le mot de passe. Sur un ordinateur n’appartenant pas au domaine, vous pouvez entrer le nom de l’ordinateur et un nom de compte d’utilisateur valide, comme <strong>MJO-DL\name@something.com</strong>, ainsi que le mot de passe correct.

11. Sur l’ordinateur Visual Studio, l’exécution doit être arrêtée au point d’arrêt.

    > [!TIP]
    > Le déploiement des fichiers peut également faire l’objet d’une autre étape. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **mymfc**, puis choisissez **Déployer**.

    Si vous avez des fichiers de code non requis par l’application, vous pouvez les spécifier dans **fichiers supplémentaires à déployer** sur le **débogueur Windows distant** page.

    Ou bien, vous pouvez inclure les fichiers dans votre projet et définir le **contenu** propriété **Oui** dans le **propriétés** page pour chaque fichier. Ces fichiers sont copiés vers le **répertoire de déploiement** spécifié sur le **débogueur Windows distant** page. Vous pouvez également modifier le **Type d’élément** à **copier le fichier** et spécifier des propriétés supplémentaires si vous avez besoin des fichiers à copier dans un sous-dossier de la **répertoire de déploiement**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurer le débogage avec des symboles distants

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Voir aussi
- [Débogage dans Visual Studio](../debugger/index.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Configurer le Pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md)
- [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)