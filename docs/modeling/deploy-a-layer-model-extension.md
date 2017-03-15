---
title: "Déployer une extension de modèle de couche | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 27
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 03164fe80a0b8f4dbc321a7e57b7db9e38e405d5
ms.lasthandoff: 02/22/2017

---
# <a name="deploy-a-layer-model-extension"></a>Déployer une extension de modèle de couche
D'autres utilisateurs de Visual Studio peuvent installer des extensions de modélisation de couche que vous créez à l'aide de Visual Studio.  
  
## <a name="installing-your-extension"></a>Installation de votre extension  
 Votre extension est compilée dans un fichier VSIX, que vous pouvez installer sur d'autres ordinateurs. Vous pouvez également l'installer sur votre ordinateur de développement, pour la rendre accessible dans l'instance principale de Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Pour installer l'extension  
  
1.  Dans le projet qui contient **source.vsix.manifest**, ouvrez **bin\\ \* ** dans l’Explorateur de fichiers.  
  
2.  Copie le ** \*.vsix** fichier sur l’ordinateur sur lequel vous souhaitez installer l’extension.  
  
3.  Sur l'ordinateur cible, double-cliquez sur le fichier *.vsix dans l'Explorateur Windows.  
  
     L'installateur VSIX s'ouvre.  
  
#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension  
  
1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.  
  
2.  Cliquez sur le nom de l’extension **désinstallation**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installation d'une extension sur un serveur Team Foundation Build  
 En général, Visual Studio n'est pas installé sur les serveurs [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]. Vous ne pouvez donc pas installer l'extension VSIX en double-cliquant dessus. L'installation de [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] inclut certains composants qui autorisent l'exécution d'une extension VSIX, mais vous devez installer l'extension manuellement.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Pour installer votre extension de couche sur un serveur [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]  
  
1.  Copie le **.vsix** fichiers à partir de votre ordinateur de développement pour la [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] ordinateur.  
  
     Placez le fichier VSIX à l'un des emplacements suivants :  
  
    -   Pour installer pour tous les utilisateurs et services :  
  
         %ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft  
  
    -   Pour installer uniquement pour le service réseau qui exécute [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] :  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version] \Extensions\Microsoft  
  
    -   Si vous avez configuré [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] pour s'exécuter en mode interactif en tant qu'utilisateur particulier, vous pouvez effectuer l'installation uniquement pour cet utilisateur :  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version] \Extensions\Microsoft  
  
        > [!NOTE]
        >  %LocalAppData% est généralement *lettre_lecteur*: utilisateurs*nom d’utilisateur*AppDataLocal.  
  
2.  Développez chaque fichier VSIX dans un dossier au même emplacement :  
  
    1.  Modifier l’extension de nom de fichier **.vsix** à **.zip**.  
  
    2.  Extrayez le contenu du fichier .zip dans un dossier.  
  
    3.  Supprimez le fichier .zip.  
  
3.  Redémarrez [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].

