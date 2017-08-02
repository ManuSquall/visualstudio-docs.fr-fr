---
title: "Comment&#160;: modifier le point pivot d’un mod&#232;le 3D | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: modifier le point pivot d’un mod&#232;le 3D
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document montre comment utiliser l'éditeur de modèle pour modifier *le point pivot* d'un modèle 3D.  Le point pivot est le point dans l'espace qui définit le centre mathématique de l'objet pour la rotation et la mise à l'échelle.  
  
 Ce document montre cette activité :  
  
-   Modification du point pivot d'un objet  
  
## Modification du point pivot d'un modèle 3D  
 Vous pouvez redéfinir l'origine d'un modèle 3D en changeant son point pivot.  
  
 Assurez\-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.  
  
#### Pour modifier le point pivot d'un modèle 3D  
  
1.  Démarrez avec un modèle 3D existant, tel que celui qui est décrit dans [Procédure : créer un modèle 3D de base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md).  
  
2.  Accédez au mode Pivot.  Dans la barre d'outils **de l'Editeur de modèles**, choisissez le bouton **Mode Pivot** pour active le mode de pivot.  Une zone apparaît autour du bouton **Mode Pivot** pour indiquer que l'Éditeur de modèle est maintenant en mode Pivot.  En mode de pivot, les opérations telles que la traduction affectent le point pivot de l'objet au lieu de la structure de l'objet dans l'espace.  
  
3.  Modifiez le point pivot de l'objet.  En mode **Select**, sélectionnez l'objet, puis dans la barre d'outils **Visionneuse de modèle**, choisissez l'outil **Traduire**.  Une zone représentant le point pivot apparaît sur l'aire de conception.  Déplacez la zone pour modifier le point de pivot de l'objet.  
  
     En déplaçant la zone, vous pouvez déplacer le point de pivot dans les trois dimensions.  Pour traduire le point pivot le long d'un axe, déplacez la flèche correspondant à cet axe.  La zone et les flèches sont remplacés par une couleur jaune pour indiquer l'axe qui est affecté par la traduction.  
  
     Vous pouvez également spécifier le point pivot à l'aide de la propriété **Déplacement du pivot** dans la fenêtre **Propriétés**.  
  
    > [!TIP]
    >  Vous pouvez afficher l'effet du nouveau point pivot en faisant tourner l'objet.  Pour le faire pivoter, utilisez l'outil **Faire pivoter** ou modifiez la propriété **Rotation**.  
  
 Ici on a un modèle dont on a mdifié le point pivot:  
  
 ![Modèle de maison ayant un point pivot modifié](~/docs/designers/media/digit-modified-model.png "Digit\-Modified\-Model")  
  
## Voir aussi  
 [Procédure : créer un modèle 3D de base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [Éditeur de modèle](../designers/model-editor.md)