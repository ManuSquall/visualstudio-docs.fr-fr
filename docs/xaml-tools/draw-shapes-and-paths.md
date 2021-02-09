---
title: Dessiner des formes et des tracés
description: Utilisez les fonctionnalités du Concepteur XAML dans Blend pour Visual Studio pour dessiner des tracés et des formes, les modifier et les combiner.
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e815b3e4959727dab282fcbe0fcd1f82890bf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847347"
---
# <a name="draw-shapes-and-paths"></a>Dessiner des formes et des tracés

Dans le concepteur XAML, une *forme* correspond exactement à ce à quoi vous pensez : un cercle, un rectangle, une ellipse, etc. Un *tracé* est une sorte de forme qui offre davantage de souplesse. Vous pouvez notamment le remodeler ou le combiner à d'autres tracés pour créer de nouvelles formes.

Les formes et les tracés font appel à des graphiques vectoriels pour mieux s’adapter aux affichages à haute résolution.

## <a name="draw-a-shape"></a>Dessiner une forme

Recherchez des formes dans la fenêtre **Composants**.

:::image type="content" source="media/blend-shapes.png" alt-text="Capture d’écran de la catégorie formes de la fenêtre composants dans Blend pour Visual Studio":::

Faites glisser la forme de votre choix vers la planche graphique. Vous pouvez ensuite utiliser les poignées de la forme pour la mettre à l’échelle, la faire pivoter, la déplacer ou l’incliner.

![Poignées](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Dessiner un tracé

Un tracé est une série de lignes et de courbes reliées. Les tracés permettent de créer des formes intéressantes qui ne sont pas disponibles dans la fenêtre **Composants**.

Vous pouvez dessiner un tracé à l'aide d'une ligne, d'une plume ou d'un crayon. Ces outils se trouvent dans la fenêtre **Outils**.

### <a name="draw-a-straight-line"></a>Tracer une ligne droite

Utilisez l’outil **Plume** ou l’outil **Ligne**.

**Utilisation de l’outil Plume**

Sur la planche graphique, cliquez une fois pour définir le point de départ et une autre fois pour définir la fin de la ligne.

**Utilisation de l’outil Ligne**

Sur la planche graphique, faites glisser le curseur du point de départ de la ligne, puis relâchez le bouton là où elle doit se terminer.

### <a name="draw-a-curve"></a>Tracer une courbe

Utilisez l’outil **Plume**.

Sur la planche graphique, cliquez une fois pour définir le point de départ d'une ligne, puis cliquez et faites glisser le pointeur pour créer la courbe souhaitée.

Si vous voulez clore le tracé, cliquez sur le premier point de la ligne.

### <a name="change-the-shape-of-a-curve"></a>Modifier la forme d'une courbe

Utilisez l’outil **Sélection directe**.

Cliquez sur la forme, puis faites glisser n'importe quel point sur la forme pour modifier les formes courbes.

### <a name="draw-a-free-form-path"></a>Dessiner un tracé de forme libre

Utilisez l’outil **Crayon**.

Sur la planche graphique, dessinez un tracé de forme libre comme vous le feriez avec un vrai crayon.

### <a name="remove-part-of-a-path"></a>Supprimer une partie d'un tracé

Utilisez l’outil **Sélection directe**.

Sélectionnez le tracé qui contient le segment à supprimer, puis cliquez sur le bouton **Supprimer** .

### <a name="remove-a-point-in-a-path"></a>Supprimer un point sur un tracé

Utilisez l’outil **Sélection** pour sélectionner le tracé. Utilisez ensuite l’outil **Plume** pour cliquer sur le point à supprimer.

### <a name="add-a-point-to-a-path"></a>Ajouter un point à un tracé

Utilisez l’outil **Sélection** pour sélectionner le tracé. Utilisez l’outil **Plume** pour cliquer à l’endroit où vous voulez ajouter le point sur le tracé.

## <a name="convert-a-shape-to-a-path"></a>Convertir une forme en tracé

Pour modifier une forme à la manière d’un tracé, convertissez la forme en tracé. Sélectionnez la forme, puis sélectionnez   >  **chemin d’accès** au format  >  **convertir en tracé**.

**Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation de tracés : convertir une forme en tracé](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

> [!NOTE]
> L’option **Convertir en tracé** n’est pas disponible pour les applications UWP qui ont une `TargetPlatformVersion` minimale de 10.0.16299.0 (ou ultérieure).

## <a name="combine-paths"></a>Combiner des tracés

Vous pouvez combiner des tracés et des formes pour en faire un seul et même tracé.

![Combiner des tracés](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Nombre|Action|
|-|-|
|![Les deux formes avant d'être combinées](../designers/media/b1_1.png)|Les deux formes avant d'être combinées|
|![Unir](../designers/media/b1_2.png)|Unir|
|![Diviser](../designers/media/b1_3.png)|Diviser|
|![Intersect](../designers/media/b1_4.png)|Intersect|
|![Exclure le chevauchement](../designers/media/b1_5.png)|Exclure le chevauchement|
|![Soustraire](../designers/media/b1_6.png)|Soustraire|

**Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation de tracés : combiner des tracés](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a>Créer un tracé composite

Quand vous créez un tracé composite, toutes les parties situées à l'intersection des tracés sont soustraites du résultat, et le tracé obtenu adopte les propriétés visuelles du tracé inférieur.

Vous pouvez à tout moment dissocier un tracé composite après l’avoir créé.

![Dissocier un tracé composite](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation de tracés : créer un tracé composite](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a>Créer un tracé de détourage

Un tracé de détourage est un tracé ou une forme qui est appliqué à un autre objet ; les parties de l’objet masqué situées à l’extérieur du tracé de détourage sont masquées.

![Tracé de détourage](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation de tracés : créer un tracé de détourage](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).
