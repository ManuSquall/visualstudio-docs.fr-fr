---
title: Déployer une extension de modèle de couche
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8614df4c8e7b3a640f7ba488ad18384886b56afe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834306"
---
# <a name="deploy-a-layer-model-extension"></a>Déployer une extension de modèle de couche

D'autres utilisateurs de Visual Studio peuvent installer des extensions de modélisation de couche que vous créez à l'aide de Visual Studio.

## <a name="install-your-extension"></a>Installer votre extension

Votre extension est compilée dans un fichier VSIX, que vous pouvez installer sur d'autres ordinateurs. Vous pouvez également l'installer sur votre ordinateur de développement, pour la rendre accessible dans l'instance principale de Visual Studio.

### <a name="to-install-the-extension"></a>Pour installer l'extension

1. Dans le projet qui contient **source.vsix.manifest**, ouvrez le *bin* répertoire dans l’Explorateur de fichiers.

2. Copie le  **\*.vsix** fichier sur l’ordinateur sur lequel vous souhaitez installer l’extension.

3. Sur l'ordinateur cible, double-cliquez sur le fichier *.vsix dans l'Explorateur Windows.

    L'installateur VSIX s'ouvre.

### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension

1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.

2.  Cliquez sur le nom de l’extension, puis **désinstallation**.

## <a name="install-an-extension-on-team-foundation-server"></a>Installer une Extension sur Team Foundation Server

Serveurs Team Foundation Server n’ont pas normalement Visual Studio est installé, et par conséquent, vous ne pouvez pas installer l’extension VSIX en double-cliquant dessus. Vous devez installer l’extension manuellement.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Pour installer votre extension de couche sur un serveur Team Foundation Server

1.  Copie le. *vsix* fichiers à partir de votre ordinateur de développement vers l’ordinateur Team Foundation Server (TFS).

     Placez le fichier VSIX à l'un des emplacements suivants :

    -   Pour installer pour tous les utilisateurs et services :

         %ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft

    -   Pour installer uniquement pour le service de réseau qui exécute la build :

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Si vous avez configuré la build s’exécute en mode interactif en tant qu’un utilisateur particulier, vous pouvez installer uniquement pour cet utilisateur :

         %LocalAppData%\Microsoft\VisualStudio\\[version] \Extensions\Microsoft

2.  Développez chaque fichier VSIX dans un dossier au même emplacement :

    1.  Modifier l’extension de nom de fichier **.vsix** à **.zip**.

    2.  Extrayez le contenu du fichier .zip dans un dossier.

    3.  Supprimez le fichier .zip.

3.  Redémarrez TFS.
