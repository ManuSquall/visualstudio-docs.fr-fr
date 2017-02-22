---
title: "Comment&#160;: appliquer un nuanceur &#224; un mod&#232;le 3D | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: appliquer un nuanceur &#224; un mod&#232;le 3D
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document montre comment utiliser l'Editeur de Modèles pour appliquer un DGSL \(Directed Graph Shader Language\) à un modèle 3D.  
  
 Ce document montre cette activité :  
  
-   Application d'un Shader à un modèle 3D  
  
## Application d'un Shader à un modèle 3D  
 Vous pouvez appliquer un effet de nuanceur à un modèle 3D pour lui donner une apparence intéressante.  
  
 Avant de commencer, assurez\-vous que la fenêtre **Propriétés** est affichée.  
  
#### Pour appliquer un nuanceur à un modèle 3D  
  
1.  Démarrez avec une scène 3D qui contient un ou plusieurs modèles.  Si vous n'avez pas de scène 3D appropriée, créez en une telle que décrit dans [Procédure : créer un modèle 3D de base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md).  Vous devez également avoir un shader DGSL applicable au modèle.  Si vous n'avez aucun shader approprié, créez en un tel que décrit dans [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md) et assurez\-vous que vous l'avez stocké dans un fichier avant de continuer.  
  
2.  En mode **Sélectionner**, sélectionnez le modèle auquel vous voulez appliquer le shader, puis dans la fenêtre **Propriétés**, dans la propriété **Nom de fichier** du groupe de propriétés **Effet**, spécifiez le shader DGSL à appliquer au modèle.  
  
 Voici un modèle auquel on a appliqué les effets de couleur de base :  
  
 ![Scène 3D illustrant l'effet de couleur de base](../designers/media/digit-3d-model-effect.png "Digit\-3D\-Model\-Effect")  
  
 Lorsque vous appliquez un shader à un modèle, vous pouvez l'ouvrir dans Shader Designer en sélectionnant le modèle, puis dans la fenêtre **Propriétés**, dans la propriété **\(Avancé\)** du groupe de propriétés **Effet**, vous choisissez le bouton d'ellipse \(**...**\).  
  
## Voir aussi  
 [Procédure : créer un modèle 3D de base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)   
 [Éditeur de modèle](../designers/model-editor.md)   
 [Concepteur Shader](../designers/shader-designer.md)