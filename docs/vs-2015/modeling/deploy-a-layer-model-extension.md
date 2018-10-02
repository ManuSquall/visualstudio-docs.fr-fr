---
title: Déployer une extension de modèle de couche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b5d581ca67a2d3fde5b7acab5937d1aedf88cfa4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495162"
---
# <a name="deploy-a-layer-model-extension"></a>Déployer une extension de modèle de couche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [déployer une extension de modèle de couche](https://docs.microsoft.com/visualstudio/modeling/deploy-a-layer-model-extension).  
  
D'autres utilisateurs de Visual Studio peuvent installer des extensions de modélisation de couche que vous créez à l'aide de Visual Studio.  
  
## <a name="installing-your-extension"></a>Installation de votre extension  
 Votre extension est compilée dans un fichier VSIX, que vous pouvez installer sur d'autres ordinateurs. Vous pouvez également l'installer sur votre ordinateur de développement, pour la rendre accessible dans l'instance principale de Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Pour installer l'extension  
  
1.  Dans le projet qui contient **source.vsix.manifest**, ouvrez **bin\\ \***  dans l’Explorateur de fichiers.  
  
2.  Copie le  **\*.vsix** fichier sur l’ordinateur sur lequel vous souhaitez installer l’extension.  
  
3.  Sur l'ordinateur cible, double-cliquez sur le fichier *.vsix dans l'Explorateur Windows.  
  
     L'installateur VSIX s'ouvre.  
  
#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension  
  
1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.  
  
2.  Cliquez sur le nom de l’extension, puis **désinstallation**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installation d'une extension sur un serveur Team Foundation Build  
 En général, Visual Studio n'est pas installé sur les serveurs [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]. Vous ne pouvez donc pas installer l'extension VSIX en double-cliquant dessus. L'installation de [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] inclut certains composants qui autorisent l'exécution d'une extension VSIX, mais vous devez installer l'extension manuellement.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>Pour installer votre extension de couche sur un serveur [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]  
  
1.  Copie le **.vsix** fichiers à partir de votre ordinateur de développement pour le [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] ordinateur.  
  
     Placez le fichier VSIX à l'un des emplacements suivants :  
  
    -   Pour installer pour tous les utilisateurs et services :  
  
         %ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft  
  
    -   Pour installer uniquement pour le service réseau qui exécute [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] :  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Si vous avez configuré [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] pour s'exécuter en mode interactif en tant qu'utilisateur particulier, vous pouvez effectuer l'installation uniquement pour cet utilisateur :  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version] \Extensions\Microsoft  
  
        > [!NOTE]
        >  %LocalAppData% est généralement *nom_lecteur*: utilisateurs*nom d’utilisateur*AppDataLocal.  
  
2.  Développez chaque fichier VSIX dans un dossier au même emplacement :  
  
    1.  Modifier l’extension de nom de fichier **.vsix** à **.zip**.  
  
    2.  Extrayez le contenu du fichier .zip dans un dossier.  
  
    3.  Supprimez le fichier .zip.  
  
3.  Redémarrez [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].



