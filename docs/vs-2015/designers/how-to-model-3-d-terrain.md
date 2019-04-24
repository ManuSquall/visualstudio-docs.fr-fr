---
title: 'Procédure : Modéliser un Terrain 3D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c9d088be89e2cf963df65a0163713c297615121
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097477"
---
# <a name="how-to-model-3-d-terrain"></a>Procédure : Terrain 3D de modèle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce document montre comment utiliser l’éditeur de modèle pour créer un modèle de terrain 3D.  
  
 Ce document illustre ces activités :  
  
- Ajout d’objets à une scène  
  
- Sélection des faces et des points  
  
- Translation des sélections  
  
- Utilisation de l’outil **Subdiviser la face**  
  
- Tramage d’un objet dans l’aire de conception  
  
## <a name="creating-a-3-d-terrain-model"></a>Création d’un modèle de terrain 3D  
 Vous pouvez créer un terrain 3D en subdivisant un plan pour obtenir des faces supplémentaires, puis en manipulant leurs sommets pour créer des caractéristiques de terrain intéressantes.  
  
 Lorsque vous avez terminé, le modèle doit se présenter comme suit :  
  
 ![Scène 3D illustrant un modèle de terrain](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
 Avant de commencer, assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>Pour créer un modèle de terrain 3D  
  
1. Créez un modèle 3D à utiliser. Pour plus d’informations sur l’ajout d’un modèle à votre projet, consultez la section Getting Started (Prise en main) de l’article [Model Editor (Éditeur de modèle)](../designers/model-editor.md).  
  
2. Ajoutez un plan à la scène. Dans la **Boîte à outils**, sous **Formes**, sélectionnez **Plan** et déplacez-le vers l’aire de conception.  
  
   > [!TIP]
   >  Pour faciliter l’utilisation de l’objet plan, vous pouvez l’encadrer dans l’aire de conception. En mode **Sélection**, sélectionnez l’objet plan, puis dans la barre d’outils de l’éditeur de modèle, choisissez le bouton **Frame Object (Encadrer l’objet)**.  
  
3. Passez en mode de sélection de la face. Dans la barre d’outils de l’éditeur de modèle, choisissez **Sélectionner la face**.  
  
4. Subdivisez le plan. En mode de sélection de la face, choisissez le plan une fois pour l’activer pour la sélection, puis choisissez-le à nouveau pour sélectionner uniquement sa face. Dans la barre d’outils de l’éditeur de modèle, choisissez **Subdiviser la face**. De nouveaux sommets sont ajoutés au plan qui le fractionnent en quatre partitions de même taille.  
  
5. Créez d’autres subdivisions. Les nouvelles faces étant toujours sélectionnées, choisissez **Subdiviser la face** deux autres fois. Au total, 64 faces sont créées. En créant d’autres subdivisions, vous pouvez donner au terrain encore plus de détails.  
  
6. Passez en mode de sélection du point. Dans la barre d’outils de l’éditeur de modèle, choisissez **Sélectionner le point**.  
  
7. Modifiez un point pour créer une caractéristique de terrain. En mode de sélection du point, sélectionnez l’un des points, puis, dans la barre d’outils de l’éditeur de modèle, choisissez l’outil **Translater**. Une zone représentant le point s’affiche sur l’aire de conception. Utilisez la flèche verte pour déplacer la zone et ainsi modifier la hauteur du point. Répétez cette étape pour différents points afin de créer des caractéristiques intéressantes de terrain.  
  
   > [!TIP]
   >  Vous pouvez sélectionner plusieurs points à la fois pour les modifier de manière uniforme.  
  
   Le modèle de terrain est terminé. Voici à nouveau le modèle final, avec l’ombrage Phong appliqué :  
  
   ![Scène 3D illustrant un modèle de terrain](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
   Vous pouvez utiliser ce modèle de terrain pour montrer l’effet du nuanceur de dégradé décrit dans [Guide pratique pour Créer un nuanceur de dégradé Geometry](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle](../designers/model-editor.md)
