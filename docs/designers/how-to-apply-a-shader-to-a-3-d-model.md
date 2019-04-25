---
title: 'Procédure : Appliquer un nuanceur à un modèle 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 896cc39ae3e9f53d96a30f6485c40afc8259e270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845042"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Procédure : Appliquer un nuanceur à un modèle 3D

Cet article montre comment utiliser l’éditeur de modèle pour appliquer un nuanceur DGSL (Directed Graph Shader Language) à un modèle 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Appliquer un nuanceur à un modèle 3D

Vous pouvez appliquer un effet de nuanceur à un modèle 3D pour lui donner une apparence intéressante.

Avant de commencer, assurez-vous que la fenêtre **Propriétés** est affichée.

1. Commencez par une scène 3D contenant un ou plusieurs modèles. Si vous ne disposez pas d’une scène 3D appropriée, créez-en une comme décrit dans l’article [Guide pratique pour créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md). Vous devez également disposer d’un nuanceur DGSL que vous pouvez appliquer au modèle. Si vous n’avez pas de nuanceur approprié, créez-en un comme décrit dans [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md) et vérifiez que vous l’avez enregistré dans un fichier avant de continuer.

2. En mode **Sélection**, sélectionnez le modèle que vous souhaitez appliquer au nuanceur puis, dans la fenêtre **Propriétés**, dans la propriété **Nom de fichier** du groupe de propriétés **Effet**, spécifiez le nuanceur DGSL à appliquer au modèle.

Exemple de modèle auquel l’effet de couleur de base est appliqué :

![Scène 3D montrant l’effet de couleur de base](../designers/media/digit-3d-model-effect.png)

Après avoir appliqué un nuanceur à un modèle, vous pouvez l’ouvrir dans le Concepteur de nuanceur en sélectionnant le modèle, puis, dans la fenêtre **Propriétés**, dans la propriété **(Avancé)** du groupe de propriétés **Effet**, en choisissant le bouton de sélection (**...** ).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md)
- [Guide pratique pour créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md).
- [Éditeur de modèles](../designers/model-editor.md)
- [Concepteur Shader](../designers/shader-designer.md)