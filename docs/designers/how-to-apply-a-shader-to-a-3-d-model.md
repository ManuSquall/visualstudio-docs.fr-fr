---
title: "Comment : appliquer un nuanceur à un modèle 3D | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: adec7e86fcb33985aa61b7e20b7e9ac16d2ad7b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Comment : appliquer un nuanceur à un modèle 3D
Ce document indique comment utiliser l’éditeur de modèle pour appliquer un nuanceur DGSL (Directed Graph Shader Language) à un modèle 3D.  
  
 Ce document illustre cette activité :  
  
-   Application d’un nuanceur à un modèle 3D  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>Application d’un nuanceur à un modèle 3D  
 Vous pouvez appliquer un effet de nuanceur à un modèle 3D pour lui donner une apparence intéressante.  
  
 Avant de commencer, assurez-vous que la fenêtre **Propriétés** est affichée.  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Pour appliquer un nuanceur à un modèle 3D  
  
1.  Commencez par une scène 3D contenant un ou plusieurs modèles. Si vous ne disposez pas d’une scène 3D appropriée, créez-en une en suivant la description de l’article [Comment : créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md). Vous devez également disposer d’un nuanceur DGSL que vous pouvez appliquer au modèle. Si vous ne disposez pas d’un nuanceur approprié, créez-en un en suivant la description de l’article [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md) et veillez à l’enregistrer dans un fichier avant de continuer.  
  
2.  En mode **Sélection**, sélectionnez le modèle que vous souhaitez appliquer au nuanceur, puis, dans la fenêtre **Propriétés**, dans la propriété **Nom de fichier** du groupe de propriétés **Effet**, spécifiez le nuanceur DGSL à appliquer au modèle.  
  
 Exemple de modèle auquel l’effet de couleur de base est appliqué :  
  
 ![Scène 3D illustrant l’effet de couleur de base](../designers/media/digit-3d-model-effect.png "Digit-3D-Model-Effect")  
  
 Après avoir appliqué un nuanceur à un modèle, vous pouvez l’ouvrir dans le Concepteur de nuanceur en sélectionnant le modèle, puis, dans la fenêtre **Propriétés**, dans la propriété **(Avancé)** du groupe de propriétés **Effet**, en choisissant le bouton de sélection (**...** ).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md)   
 [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)   
 [Éditeur de modèle](../designers/model-editor.md)   
 [Concepteur de nuanceur](../designers/shader-designer.md)