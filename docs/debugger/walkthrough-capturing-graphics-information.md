---
title: "Proc&#233;dure pas &#224; pas&#160;: capture d&#39;informations Graphics | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Proc&#233;dure pas &#224; pas&#160;: capture d&#39;informations Graphics
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment utiliser Graphics Diagnostics dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour capturer manuellement les informations graphiques d’une application Direct3D.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Raccordement de Graphics Diagnostics à votre application  
  
-   Capture d'informations graphiques  
  
## Capture d'informations graphiques  
 Pour utiliser les outils Graphics Diagnostics, vous devez d'abord capturer les informations graphiques dont ils ont besoin. Pour activer la capture, utilisez la commande **Démarrer les diagnostics** pour raccorder Graphics Diagnostics à votre application lors de son démarrage.  
  
#### Pour activer la capture des informations graphiques après le chargement d’un projet ou d’une solution  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], chargez un fichier projet ou solution pour l’application dont vous souhaitez capturer les informations graphiques.  
  
2.  Dans la barre d’outils Graphics Diagnostics, choisissez **Démarrer les diagnostics**.  
  
#### Pour activer la capture des informations graphiques sans charger de projet ou solution  
  
1.  Dans la barre de menus, choisissez **Fichier**, **Ouvrir**, **Projet\/Solution**. La boîte de dialogue **Ouvrir un projet** s’affiche.  
  
2.  Au lieu d’un fichier projet ou solution, spécifiez le fichier exécutable de l’application dont vous voulez capturer les informations graphiques, puis choisissez **Ouvrir**.  
  
3.  Dans la barre de menus, choisissez **Déboguer**, **Graphiques**, **Démarrer les diagnostics**.  
  
 Après le démarrage de l’application et l’affichage des frames, vous pouvez commencer la capture des informations graphiques.  
  
#### Pour capturer des informations graphiques  
  
-   Dans la barre d’outils Graphics Diagnostics, choisissez le bouton **Capturer**.![Icône du bouton de capture de graphiques](~/debugger/graphics/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     ou  
  
     Quand l’application a le focus, appuyez sur **Impr. écran**.  
  
 Chaque fois que vous capturez des informations sur un frame, Graphics Diagnostics enregistre les événements Direct3D et leur état associé, puis ajoute ces données dans un journal de graphisme. Un nouveau journal de graphisme est créé pour chaque session Graphics Diagnostics. Pour plus d’informations sur les journaux de graphisme, consultez [Vue d'ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Étapes suivantes  
 Cette procédure pas à pas vous a montré comment capturer manuellement des informations graphiques. Pour franchir une étape supplémentaire, envisagez cette possibilité :  
  
-   Découvrez comment analyser les informations graphiques capturées à l’aide des outils Graphics Diagnostics. Consultez [Vue d'ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Voir aussi  
 [Capture d'informations Graphics](../debugger/capturing-graphics-information.md)