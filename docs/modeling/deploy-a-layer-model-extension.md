---
title: Déployer une extension de modèle de couche | Documents Microsoft
ms.custom: ''
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
ms.technology: vs-ide-modeling
ms.openlocfilehash: 95cfb5fa4764c53c14e5884cf41165f61a063337
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-a-layer-model-extension"></a>Déployer une extension de modèle de couche
D'autres utilisateurs de Visual Studio peuvent installer des extensions de modélisation de couche que vous créez à l'aide de Visual Studio.  
  
## <a name="installing-your-extension"></a>Installation de votre extension  
 Votre extension est compilée dans un fichier VSIX, que vous pouvez installer sur d'autres ordinateurs. Vous pouvez également l'installer sur votre ordinateur de développement, pour la rendre accessible dans l'instance principale de Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Pour installer l'extension  
  
1.  Dans le projet qui contient **source.vsix.manifest**, ouvrez **bin\\ \***  dans l’Explorateur de fichiers.  
  
2.  Copie le  **\*.vsix** fichier à l’ordinateur sur lequel vous souhaitez installer l’extension.  
  
3.  Sur l'ordinateur cible, double-cliquez sur le fichier *.vsix dans l'Explorateur Windows.  
  
     L'installateur VSIX s'ouvre.  
  
#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension  
  
1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.  
  
2.  Cliquez sur le nom de l’extension, puis **désinstallation**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installation d'une extension sur un serveur Team Foundation Build  
 En général, Visual Studio n'est pas installé sur les serveurs [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]. Vous ne pouvez donc pas installer l'extension VSIX en double-cliquant dessus. L'installation de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] inclut certains composants qui autorisent l'exécution d'une extension VSIX, mais vous devez installer l'extension manuellement.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Pour installer votre extension de couche sur un serveur [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]  
  
1.  Copie le **.vsix** fichiers à partir de votre ordinateur de développement pour la [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] ordinateur.  
  
     Placez le fichier VSIX à l'un des emplacements suivants :  
  
    -   Pour installer pour tous les utilisateurs et services :  
  
         %ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft  
  
    -   Pour installer uniquement pour le service réseau qui exécute [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] :  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Si vous avez configuré [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] pour s'exécuter en mode interactif en tant qu'utilisateur particulier, vous pouvez effectuer l'installation uniquement pour cet utilisateur :  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version] \Extensions\Microsoft  
  
        > [!NOTE]
        >  %LocalAppData% est généralement *%drivename*: les utilisateurs*nom d’utilisateur*AppDataLocal.  
  
2.  Développez chaque fichier VSIX dans un dossier au même emplacement :  
  
    1.  Modifier l’extension de nom de fichier **.vsix** à **.zip**.  
  
    2.  Extrayez le contenu du fichier .zip dans un dossier.  
  
    3.  Supprimez le fichier .zip.  
  
3.  Redémarrez [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
