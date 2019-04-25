---
title: Dessiner des formes et des tracés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c30b0a190d2a2abfed56004e167f6ee5ef5ecf97
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046071"
---
# <a name="draw-shapes-and-paths"></a>Dessiner des formes et des tracés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le concepteur XAML, une *forme* correspond exactement à ce à quoi vous pensez : un cercle, un rectangle, une ellipse, etc. Un *tracé* est une sorte de forme qui offre davantage de souplesse. Vous pouvez notamment le remodeler ou le combiner à d'autres tracés pour créer de nouvelles formes.  
  
 Les formes et les tracés font appel à des graphiques vectoriels pour mieux s’adapter aux affichages à haute résolution. Pour en savoir plus sur les graphiques vectoriels, regardez la vidéo [What are Vector Graphics](https://www.youtube.com/watch?v=MoCSwF0n-io) (Présentation des graphiques vectoriels) ou lisez la définition des [graphiques vectoriels](http://www.webopedia.com/TERM/V/vector_graphics.html).  
  
 **Dans cette rubrique :**  
  
- [Dessiner une forme](#Shape)  
  
- [Dessiner un tracé](#Path)  
  
- [Convertir une forme en tracé](#Convert)  
  
- [Combiner des tracés](#Combine)  
  
- [Créer un tracé composite](#Compound)  
  
- [Créer un tracé de détourage](#Clipping)  
  
## <a name="Shape"></a> Dessiner une forme  
 Vous pouvez trouver des formes dans le panneau **Composants** .  
  
 ![Catégorie Formes du volet Composants](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")  
  
 Faites glisser la forme de votre choix vers la planche graphique. Vous pouvez ensuite utiliser les poignées de la forme pour la mettre à l'échelle, la faire pivoter, la déplacer ou l'incliner.  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-AB58-4218b188439e")  
  
## <a name="Path"></a> Dessiner un tracé  
 Un tracé est une série de lignes et de courbes reliées. Les tracés permettent de créer des formes intéressantes qui ne sont pas disponibles dans le panneau **Composants** .  
  
 Vous pouvez dessiner un tracé à l'aide d'une ligne, d'une plume ou d'un crayon. Ces outils se trouvent dans le panneau **Outils** .  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8AF3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")  
  
### <a name="draw-a-straight-line"></a>Tracer une ligne droite  
 Utilisez l’outil **Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") ou l’outil **Ligne** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf").  
  
 **Utilisation de l’outil Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")  
  
 Sur la planche graphique, cliquez une fois pour définir le point de départ et une autre fois pour définir la fin de la ligne.  
  
 **Utilisation de l’outil Ligne** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")  
  
 Sur la planche graphique, faites glisser le curseur du point de départ de la ligne, puis relâchez le bouton là où elle doit se terminer.  
  
### <a name="draw-a-curve"></a>Tracer une courbe  
 **Utilisez l’outil Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Sur la planche graphique, cliquez une fois pour définir le point de départ d'une ligne, puis cliquez et faites glisser le pointeur pour créer la courbe souhaitée.  
  
 Si vous voulez clore le tracé, cliquez sur le premier point de la ligne.  
  
### <a name="change-the-shape-of-a-curve"></a>Modifier la forme d'une courbe  
 Utilisez l’outil **Sélection directe** ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Cliquez sur la forme, puis faites glisser n'importe quel point sur la forme pour modifier les formes courbes.  
  
### <a name="draw-a-free-form-path"></a>Dessiner un tracé de forme libre  
 Utilisez l’outil **Crayon** ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd").  
  
 Sur la planche graphique, dessinez un tracé de forme libre comme vous le feriez avec un vrai crayon.  
  
### <a name="remove-part-of-a-path"></a>Supprimer une partie d'un tracé  
 Utilisez l’outil **Sélection directe** ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Sélectionnez le tracé qui contient le segment à supprimer, puis cliquez sur le bouton **Supprimer** .  
  
### <a name="remove-a-point-in-a-path"></a>Supprimer un point sur un tracé  
 Utilisez l’outil **Sélection** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") et l’outil **Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Utilisez l’outil **Sélection** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") pour sélectionner le chemin. Ensuite, utilisez l’outil **Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") pour cliquer sur le point que vous souhaitez supprimer.  
  
### <a name="add-a-point-to-a-path"></a>Ajouter un point à un tracé  
 Utilisez l’outil **Sélection** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") et l’outil **Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Utilisez l’outil **Sélection** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") pour sélectionner le chemin. Utilisez l’outil **Plume** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") pour cliquer à l’endroit où vous voulez ajouter le point sur le tracé.  
  
## <a name="Convert"></a> Convertir une forme en tracé  
 Pour modifier une forme à la manière d’un tracé, convertissez la forme en tracé.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [utilisation des tracés : convertir une forme en tracé](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).  
  
## <a name="Combine"></a> Combiner des tracés  
 Vous pouvez combiner des tracés et des formes pour en faire un seul et même tracé.  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-A338-4ef4-96c5-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1-1.png "B1_1")|Les deux formes avant d'être combinées|![](../designers/media/b1-4.png "B1_4")|Définir une intersection|  
|![](../designers/media/b1-2.png "B1_2")|Unir|![](../designers/media/b1-5.png "B1_5")|Exclure le chevauchement|  
|![](../designers/media/b1-3.png "B1_3")|Diviser|![](../designers/media/b1-6.png "B1_6")|Soustraire|  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [utilisation des tracés : combiner des tracés](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).  
  
## <a name="Compound"></a> Créer un tracé composite  
 Quand vous créez un tracé composite, toutes les parties situées à l'intersection des tracés sont soustraites du résultat, et le tracé obtenu adopte les propriétés visuelles du tracé inférieur.  
  
 Vous pouvez à tout moment dissocier un tracé composite après l’avoir créé.  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [utilisation des tracés : créer un tracé composite](https://www.youtube.com/watch?v=Io5bC0-nH6Q).  
  
## <a name="Clipping"></a> Créer un tracé de détourage  
 Un tracé de détourage est un tracé ou une forme qui est appliqué à un autre objet ; les parties de l’objet masqué situées à l’extérieur du tracé de détourage sont masquées.  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-A841-4f39-a3ef-36090cf5a625")  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [utilisation des tracés : créer un tracé de détourage](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
