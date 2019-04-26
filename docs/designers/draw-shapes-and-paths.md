---
title: Dessiner des formes et des tracés
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e0efd4b4f9fb301f5bcba4a12857647a8d911f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899334"
---
# <a name="draw-shapes-and-paths"></a>Dessiner des formes et des tracés

Dans le concepteur XAML, une *forme* correspond exactement à ce à quoi vous pensez : un cercle, un rectangle, une ellipse, etc. Un *tracé* est une sorte de forme qui offre davantage de souplesse. Vous pouvez notamment le remodeler ou le combiner à d'autres tracés pour créer de nouvelles formes.

Les formes et les tracés font appel à des graphiques vectoriels pour mieux s’adapter aux affichages à haute résolution. Pour en savoir plus sur les graphiques vectoriels, regardez la vidéo [What are Vector Graphics](https://www.youtube.com/watch?v=MoCSwF0n-io) (Présentation des graphiques vectoriels) ou lisez la définition des [graphiques vectoriels](http://www.webopedia.com/TERM/V/vector_graphics.html).

## <a name="Shape"></a> Dessiner une forme
 Vous pouvez trouver des formes dans le panneau **Composants** .

 ![Catégorie Formes du volet Composants](../designers/media/b4_shapes_assetspanel.png)

 Faites glisser la forme de votre choix vers la planche graphique. Vous pouvez ensuite utiliser les poignées de la forme pour la mettre à l'échelle, la faire pivoter, la déplacer ou l'incliner.

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="Path"></a> Dessiner un tracé
 Un tracé est une série de lignes et de courbes reliées. Les tracés permettent de créer des formes intéressantes qui ne sont pas disponibles dans le panneau **Composants** .

 Vous pouvez dessiner un tracé à l'aide d'une ligne, d'une plume ou d'un crayon. Ces outils se trouvent dans le panneau **Outils** .

 ![Outil Plume](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![Options de l’outil Plume](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>Tracer une ligne droite
 Utilisez l’outil **Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) ou l’outil **Ligne** ![outil Ligne](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png).

 **Utilisation de l’outil Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 Sur la planche graphique, cliquez une fois pour définir le point de départ et une autre fois pour définir la fin de la ligne.

 **Utilisation de l’outil Ligne** ![outil Ligne](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 Sur la planche graphique, faites glisser le curseur du point de départ de la ligne, puis relâchez le bouton là où elle doit se terminer.

### <a name="draw-a-curve"></a>Tracer une courbe
 Utilisez l’outil **Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Sur la planche graphique, cliquez une fois pour définir le point de départ d'une ligne, puis cliquez et faites glisser le pointeur pour créer la courbe souhaitée.

 Si vous voulez clore le tracé, cliquez sur le premier point de la ligne.

### <a name="change-the-shape-of-a-curve"></a>Modifier la forme d'une courbe
 Utilisez l’outil **Sélection directe** ![outil Sélection directe](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Cliquez sur la forme, puis faites glisser n'importe quel point sur la forme pour modifier les formes courbes.

### <a name="draw-a-free-form-path"></a>Dessiner un tracé de forme libre
 Utilisez l’outil **Crayon** ![outil Crayon](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png).

 Sur la planche graphique, dessinez un tracé de forme libre comme vous le feriez avec un vrai crayon.

### <a name="remove-part-of-a-path"></a>Supprimer une partie d'un tracé
 Utilisez l’outil **Sélection directe** ![outil Sélection directe](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Sélectionnez le tracé qui contient le segment à supprimer, puis cliquez sur le bouton **Supprimer** .

### <a name="remove-a-point-in-a-path"></a>Supprimer un point sur un tracé
 Utilisez l’outil **Sélection** ![outil Sélection](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) et l’outil **Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Utilisez l’outil **Sélection** ![outil Sélection](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) pour sélectionner le tracé. Utilisez ensuite l’outil **Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) pour cliquer sur le point à supprimer.

### <a name="add-a-point-to-a-path"></a>Ajouter un point à un tracé
 Utilisez l’outil **Sélection** ![outil Sélection](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) et l’outil **Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Utilisez l’outil **Sélection** ![outil Sélection](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) pour sélectionner le tracé. Utilisez l’outil **Plume** ![outil Plume](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) pour cliquer à l’endroit où vous voulez ajouter le point sur le tracé.

## <a name="Convert"></a> Convertir une forme en tracé
 Pour modifier une forme à la manière d’un tracé, convertissez la forme en tracé.

 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation des tracés : convertir une forme en tracé](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="Combine"></a> Combiner des tracés
 Vous pouvez combiner des tracés et des formes pour en faire un seul et même tracé.

 ![Combiner des tracés](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![Les deux formes avant d'être combinées](../designers/media/b1_1.png)|Les deux formes avant d'être combinées|![Définir une intersection](../designers/media/b1_4.png)|Définir une intersection|
|![Exclure le chevauchement](../designers/media/b1_2.png)|Unir|![](../designers/media/b1_5.png)|Exclure le chevauchement|
|![Soustraire](../designers/media/b1_3.png)|Diviser|![](../designers/media/b1_6.png)|Soustraire|

 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation des tracés : combiner des tracés](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="Compound"></a> Créer un tracé composite
 Quand vous créez un tracé composite, toutes les parties situées à l'intersection des tracés sont soustraites du résultat, et le tracé obtenu adopte les propriétés visuelles du tracé inférieur.

 Vous pouvez à tout moment dissocier un tracé composite après l’avoir créé.

 ![Dissocier un tracé composite](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation des tracés : créer un tracé composite](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="Clipping"></a> Créer un tracé de détourage
 Un tracé de détourage est un tracé ou une forme qui est appliqué à un autre objet ; les parties de l’objet masqué situées à l’extérieur du tracé de détourage sont masquées.

 ![Tracé de détourage](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [Utilisation des tracés : créer un tracé de détourage](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Voir aussi

- [Création d’une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)