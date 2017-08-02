---
title: "Proc&#233;dure&#160;: mod&#233;liser un terrain&#160;3D | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 17
---
# Proc&#233;dure&#160;: mod&#233;liser un terrain&#160;3D
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document montre comment utiliser l'Editeur de modèles pour créer un modèle de terrain 3\-D.  
  
 Ce document démontre les activités suivantes :  
  
-   Ajout d'objets à une scène  
  
-   Sélectionnez les faces et les points  
  
-   Traduction des selections  
  
-   À l'aide de l'outil **Subdivisez face**  
  
-   Cadrage d'un objet dans l'aire de conception  
  
## Création d'un modèle terrain 3D  
 Vous pouvez créer un terrain 3D en subdivisant un plan pour créer des faces supplémentaires, puis en manipulant leurs sommets pour créer les fonctionnalités de terrain intéressantes.  
  
 Lorsque vous avez terminé, le modèle doit se présenter de la manière suivante :  
  
 ![Scène 3&#45;D illustrant un modèle de terrain](~/docs/designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Avant de commencer, assurez\-vous que la fenêtre **Propriétés** et que la **Boîte à outils** sont affichées.  
  
#### Pour créer un modèle de terrain 3D  
  
1.  Créer un modèle 3D à utiliser.  Pour obtenir des informations sur l'ajout d'un modèle à votre projet, consultez la section Mise en route dans [Éditeur de modèle](../designers/model-editor.md).  
  
2.  Ajoutez un plan à la scène.  Dans **Boîte à outils**, sous **Formes**, sélectionnez **Plan** et faites glisser cette option sur l'aire de conception.  
  
    > [!TIP]
    >  Pour faciliter l'utilisation d'un objet plan, encadrez\-le dans l'aire de conception.  En mode **Selectionner**, sélectionnez l'objet plan, puis dans la barre d'outils de l'Editeur de Modèles, choisissez le bouton**Encadrer Objet**.  
  
3.  Accédez au mode de sélection de face.  Dans la barre d'outils de l'Editeur de modèles, choisissez **Sélectionner face**.  
  
4.  Subdivisez le plan.  En mode de sélection de face, sélectionnez le plan une fois pour l'activer pour la sélection, puis choisissez\- le de nouveau pour sélectionner uniquement la face.  Dans la barre d'outils de l'Editeur de modèles, choisissez **Subdiviser face**.  Cela ajoute de nouveaux sommets au plan qui le sépare en quatre partitions de meme taille.  
  
5.  Créez plus de subdivisions.  Avec les nouvelles faces toujours sélectionnées, choisissez **Subdivisez face** encore deux fois.  Cela crée un total de 64 faces.  En créant plus de sous\-divisions, vous pouvez fournir au terrain encore plus de détails.  
  
6.  Accédez au mode de sélection Point.  Dans la barre d'outils de l'Editeur de modèles, choisissez **Sélectionner Point**.  
  
7.  Modifiez un point pour créer une fonctionnalité de terrain.  En mode se selection Point, selectionnez un des points et ensuite choisissez l'outil **Traduire** dans la barre d'outils de l'Editeur de Modèles.  Une zone représentant le point apparaît sur l'aire de conception.  Utilisez la flèche verte pour déplacer la zone et pour modifier ainsi la hauteur du point.  Répétez cette étape pour différents points pour créer des fonctionnalités de terrain intéressantes.  
  
    > [!TIP]
    >  Vous pouvez sélectionner plusieurs points à la fois pour les modifier de façon uniforme.  
  
 Le modèle de terrain est maintenant terminé.  Voici encore le modèle final auquel on a appliqué le shading Phong.  
  
 ![Scène 3&#45;D illustrant un modèle de terrain](~/docs/designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Vous pouvez utiliser ce modèle de terrain pour illustrer l'effet du nuanceur de dégradé qui est décrit dans [Comment : créer un nuanceur de géométrie dégradé](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## Voir aussi  
 [Éditeur de modèle](../designers/model-editor.md)