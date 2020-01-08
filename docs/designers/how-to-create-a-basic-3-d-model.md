---
title: Guide pratique pour créer un modèle 3D de base
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce16e436172a7d369f2df8342f6b027b574056ab
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589524"
---
# <a name="how-to-create-a-basic-3d-model"></a>Guide pratique pour créer un modèle 3D de base

Cet article montre comment utiliser l’éditeur de modèle pour créer un modèle 3D de base. Les activités suivantes sont décrites :

- Ajout d’objets à une scène

- Sélection des faces et des arêtes

- Translation des sélections

- Utilisation des outils **Subdiviser la face** et **Extruder la face**

- Utilisation de la commande **Effectuer une triangulation**

## <a name="create-a-basic-3d-model"></a>Créer un modèle 3D de base
Vous pouvez utiliser l’éditeur de modèle pour créer et modifier des modèles et des scènes 3D pour votre jeu ou votre application. Les étapes suivantes indiquent comment utiliser l’éditeur de modèle pour créer un modèle 3D simplifié d’une maison. Un modèle simplifié peut être utilisé comme un substitut pour des ressources artistiques finales qui ne sont pas encore créées, comme un maillage pour la détection de collision ou comme un modèle de bas niveau de détail à utiliser lorsque l'objet qu'il représente est trop loin pour bénéficier d'un rendu plus détaillé.

Lorsque vous avez terminé, le modèle doit se présenter comme suit :

![Modèle terminé de la maison simplifiée](../designers/media/gfx_model_demo_house_final.png)

Avant de commencer, assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Pour créer un modèle 3D simplifié d’une maison

1. Créez un modèle 3D avec lequel travailler. Pour plus d’informations sur l’ajout d’un modèle à votre projet, consultez la section Getting Started (Prise en main) de l’article [Model Editor (Éditeur de modèle)](../designers/model-editor.md).

2. Ajoutez un cube à la scène. Dans la fenêtre **Boîte à outils**, sous **Formes**, sélectionnez **Cube**, puis faites glisser cette option vers l’aire de conception.

3. Passez à la sélection des faces. Dans la barre d’outils de l’éditeur de modèle, choisissez **Sélectionner la face**.

4. Subdivisez le haut du cube. En mode de sélection de face, sélectionnez le cube une fois pour l'activer pour la sélection, puis choisissez le haut du cube pour sélectionner la face supérieure. Dans la barre d’outils de l’éditeur de modèle, choisissez **Subdiviser la face**. De nouveaux sommets sont ajoutés en haut du cube qui le fractionnent en quatre partitions de même taille.

    ![Le haut du cube a été subdivisé](../designers/media/gfx_model_demo_house_subdiv.png)

5. Extrudez deux côtés adjacents du cube, par exemple, les côtés avant et droit du cube. En mode de sélection de face, sélectionnez le cube une fois pour l'activer pour la sélection, puis choisissez un côté du cube. Maintenez enfoncée la touche **Ctrl**, choisissez un autre côté du cube adjacent au côté que vous avez sélectionné en premier, puis choisissez **Extruder la face** dans la barre d’outils de l’éditeur de modèle.

    ![Les côtés du cube ont été extrudés](../designers/media/gfx_model_demo_house_extrude.png)

6. Étendez une des extrusions. Choisissez l’une des faces que vous venez d’extruder, puis, dans la barre d’outils de l’éditeur de modèle, choisissez l’outil **Translater** et déplacez le manipulateur de translation dans la même direction que l’extrusion.

    ![Un côté du cube a été plus extrudé.](../designers/media/gfx_model_demo_house_extend.png)

7. Effectuez une triangulation du modèle. Dans la barre d’outils de l’éditeur de modèle, choisissez **Avancé** > **Outils** > **Effectuer une triangulation**.

8. Créez le toit de la maison. Passez en mode de sélection d’arête en choisissant **Sélectionner le bord** dans la barre d’outils de l’éditeur de modèle, puis choisissez le cube pour l’activer. Maintenez enfoncée la touche **Ctrl** tout en sélectionnant les arêtes illustrées ici :

    ![Bords qui forment la pointe du toit](../designers/media/gfx_model_demo_house_edges.png)

    Lorsque les bords sont sélectionnés, dans la barre d’outils de l’éditeur de modèle, choisissez l’outil **Translater**, puis déplacez le manipulateur de translation au-dessus pour créer le toit de la maison.

   Le modèle de maison simplifié est terminé. Voici à nouveau le modèle final, avec l'ombrage constant appliqué :

   ![Modèle terminé de la maison simplifiée](../designers/media/gfx_model_demo_house_final.png)

   Ensuite, vous pouvez appliquer un nuanceur à ce modèle 3D. Pour plus d’informations, consultez [Guide pratique pour appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour modéliser un terrain 3D](../designers/how-to-model-3-d-terrain.md)
- [Éditeur de modèles](../designers/model-editor.md)
- [Concepteur Shader](../designers/shader-designer.md)
