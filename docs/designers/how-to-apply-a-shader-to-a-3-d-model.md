---
title: Guide pratique pour appliquer un nuanceur à un modèle 3D
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 445829c3171eeae3b483055688dcf5f77be67330
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637172"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Guide pratique pour appliquer un nuanceur à un modèle 3D

Cet article montre comment utiliser l’éditeur de modèle pour appliquer un nuanceur DGSL (Directed Graph Shader Language) à un modèle 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Appliquer un nuanceur à un modèle 3D

Vous pouvez appliquer un effet de nuanceur à un modèle 3D pour lui donner une apparence intéressante.

Avant de commencer, assurez-vous que la fenêtre **Propriétés** est affichée.

1. Commencez par une scène 3D contenant un ou plusieurs modèles. Si vous ne disposez pas d’une scène 3D appropriée, créez-en une comme décrit dans l’article [Guide pratique pour créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md). Vous devez également disposer d’un nuanceur DGSL que vous pouvez appliquer au modèle. Si vous ne disposez pas d’un nuanceur approprié, créez-en un en suivant la description de l’article [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md) et veillez à l’enregistrer dans un fichier avant de continuer.

2. En mode **Sélection**, sélectionnez le modèle que vous souhaitez appliquer au nuanceur puis, dans la fenêtre **Propriétés**, dans la propriété **Nom de fichier** du groupe de propriétés **Effet**, spécifiez le nuanceur DGSL à appliquer au modèle.

Exemple de modèle auquel l’effet de couleur de base est appliqué :

![Scène 3D montrant l’effet de couleur de base](../designers/media/digit-3d-model-effect.png)

Après avoir appliqué un nuanceur à un modèle, vous pouvez l’ouvrir dans le Concepteur de nuanceur en sélectionnant le modèle, puis, dans la fenêtre **Propriétés**, dans la propriété **(Avancé)** du groupe de propriétés **Effet**, en choisissant le bouton de sélection ( **...** ).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md)
- [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)
- [Éditeur de modèles](../designers/model-editor.md)
- [Concepteur Shader](../designers/shader-designer.md)