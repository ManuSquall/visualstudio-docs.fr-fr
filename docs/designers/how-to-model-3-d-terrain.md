---
title: Guide pratique pour modéliser un terrain 3D
description: Apprenez à utiliser l’éditeur de modèle pour créer un modèle de terrain 3D en divisant un plan pour faire des visages supplémentaires et manipuler leurs sommets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 969dd229d8d6cd6bdbe9d53eaabd63f1eedd6570
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930848"
---
# <a name="how-to-model-3d-terrain"></a>Guide pratique pour modéliser un terrain 3D

Cet article montre comment utiliser l’éditeur de modèle pour créer un modèle de terrain 3D.

## <a name="create-a-3d-terrain-model"></a>Créer un modèle de terrain 3D

Vous pouvez créer un terrain 3D en subdivisant un plan pour obtenir des faces supplémentaires, puis en manipulant leurs sommets pour créer des caractéristiques de terrain intéressantes.

Lorsque vous avez terminé, le modèle doit se présenter comme suit :

![Scène 3D illustrant un modèle de terrain](../designers/media/digit-terrain-model.png)

Avant de commencer, assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.

1. Créez un modèle 3D avec lequel travailler. Pour plus d’informations sur l’ajout d’un modèle à votre projet, consultez la section Prise en main dans l' [éditeur de modèle](../designers/model-editor.md).

2. Ajoutez un plan à la scène. Dans la **Boîte à outils**, sous **Formes**, sélectionnez **Plan** et déplacez-le vers l’aire de conception.

    > [!TIP]
    > Pour faciliter l’utilisation de l’objet plan, vous pouvez l’encadrer dans l’aire de conception. En mode **Sélection**, sélectionnez l’objet plan, puis dans la barre d’outils de l’éditeur de modèle, choisissez le bouton **Frame Object (Encadrer l’objet)**.

3. Passez en mode de sélection de la face. Dans la barre d’outils de l’éditeur de modèle, choisissez **Sélectionner la face**.

4. Subdivisez le plan. En mode de sélection de la face, choisissez le plan une fois pour l’activer pour la sélection, puis choisissez-le à nouveau pour sélectionner uniquement sa face. Dans la barre d’outils de l’éditeur de modèle, choisissez **Subdiviser la face**. De nouveaux sommets sont ajoutés au plan qui le fractionnent en quatre partitions de même taille.

5. Créez d’autres subdivisions. Les nouvelles faces étant toujours sélectionnées, choisissez **Subdiviser la face** deux autres fois. Au total, 64 faces sont créées. En créant d’autres subdivisions, vous pouvez donner au terrain encore plus de détails.

6. Passez en mode de sélection du point. Dans la barre d’outils de l’éditeur de modèle, choisissez **Sélectionner le point**.

7. Modifiez un point pour créer une caractéristique de terrain. En mode de sélection du point, sélectionnez l’un des points, puis, dans la barre d’outils de l’éditeur de modèle, choisissez l’outil **Translater**. Une zone représentant le point s’affiche sur l’aire de conception. Utilisez la flèche verte pour déplacer la zone et ainsi modifier la hauteur du point. Répétez cette étape pour différents points afin de créer des caractéristiques intéressantes de terrain.

    > [!TIP]
    > Vous pouvez sélectionner plusieurs points à la fois pour les modifier de manière uniforme.

Le modèle de terrain est terminé. Voici à nouveau le modèle final, avec l’ombrage Phong appliqué :

![Scène 3D illustrant un modèle de terrain](../designers/media/digit-terrain-model.png)

Vous pouvez utiliser ce modèle de terrain pour illustrer l’effet du nuanceur de dégradé décrit dans [How to : Create a Geometry gradient Shader](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur de modèle](../designers/model-editor.md)
