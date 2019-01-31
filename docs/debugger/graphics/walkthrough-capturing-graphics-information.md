---
title: 'Procédure pas à pas : Capture d’informations graphiques | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68ad8e09558aad1b6a4172acd0aa8b4749661854
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930106"
---
# <a name="walkthrough-capturing-graphics-information"></a>Procédure pas à pas : Capture d'informations graphiques
Cette procédure pas à pas montre comment utiliser Graphics Diagnostics dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour capturer manuellement les informations graphiques d’une application Direct3D.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Raccordement de Graphics Diagnostics à votre application  
  
-   Capture d'informations graphiques  
  
## <a name="capturing-graphics-information"></a>Capture d'informations graphiques  
 Pour utiliser les outils Graphics Diagnostics, vous devez d'abord capturer les informations graphiques dont ils ont besoin. Pour activer la capture, utilisez la commande **Démarrer les diagnostics** pour raccorder Graphics Diagnostics à votre application lors de son démarrage.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Pour activer la capture des informations graphiques après le chargement d’un projet ou d’une solution  
  
1. Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], chargez un fichier projet ou solution pour l’application dont vous souhaitez capturer les informations graphiques.  
  
2. Dans la barre d’outils Graphics Diagnostics, choisissez **Démarrer les diagnostics**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Pour activer la capture des informations graphiques sans charger de projet ou solution  
  
1. Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet/Solution**. La boîte de dialogue **Ouvrir un projet** s’affiche.  
  
2. Au lieu d’un fichier projet ou solution, spécifiez le fichier exécutable de l’application dont vous voulez capturer les informations graphiques, puis choisissez **Ouvrir**.  
  
3. Dans la barre de menus, choisissez **Déboguer**, **Graphiques**, **Démarrer les diagnostics**.  
  
   Après le démarrage de l’application et l’affichage des frames, vous pouvez commencer la capture des informations graphiques.  
  
#### <a name="to-capture-graphics-information"></a>Pour capturer des informations graphiques  
  
- Dans la barre d’outils Graphics Diagnostics, choisissez le bouton **Capturer** . ![Icône de bouton de capture de Graphics](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
   - ou -  
  
   Quand l’application a le focus, appuyez sur **Impr. écran**.  
  
  Chaque fois que vous capturez des informations sur un frame, Graphics Diagnostics enregistre les événements Direct3D et leur état associé, puis ajoute ces données dans un journal de graphisme. Un nouveau journal de graphisme est créé pour chaque session Graphics Diagnostics. Pour plus d’informations sur les journaux de graphisme, consultez [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas vous a montré comment capturer manuellement des informations graphiques. Pour franchir une étape supplémentaire, envisagez cette possibilité :  
  
-   Découvrez comment analyser les informations graphiques capturées à l’aide des outils Graphics Diagnostics. Consultez [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Capturing Graphics Information](capturing-graphics-information.md)