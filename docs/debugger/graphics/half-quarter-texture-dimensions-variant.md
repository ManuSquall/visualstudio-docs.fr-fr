---
title: Variante de dimensions de texture Half-Quarter | Microsoft Docs
description: Si les textures plus petites présentent des gains de performances importants, elle suggère une sollicitation de la bande passante de mémoire ou une utilisation inefficace du cache de texture GPU. Envisagez de réduire la taille des textures.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87add3c771fdc79e4b41658a68ef7e77e2c18b21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888522"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Variante de dimensions de la texture moitié/un quart
Réduit les dimensions des textures qui ne sont pas des cibles de rendu.

## <a name="interpretation"></a>Interprétation
 Les textures de plus petite taille occupent moins de mémoire et consomment ainsi moins de bande passante de mémoire et soulagent le cache de texture du GPU. Cependant, leur faible définition peut se traduire par une qualité d'image réduite, plus particulièrement sur les plans rapprochés dans une scène 3D ou dans une vue agrandie.

 Si cette variante donne lieu à un gain de performances sensible, cela peut indiquer que votre application consomme trop de bande passante de mémoire, qu'elle n'utilise pas efficacement le cache de texture, ou les deux à la fois. Cela peut aussi être le signe que vos textures occupent plus de mémoire GPU que vous n'en disposez, ce qui provoque leur pagination en mémoire système.

 Si votre application consomme trop de bande passante de mémoire ou n'utilise pas efficacement le cache de texture, songez à réduire la taille de votre textures, mais seulement après avoir envisagé d'activer les mipmaps pour les textures appropriées. Comme les textures de petite taille, les textures mipmappées consomment moins de bande passante de mémoire (même si elles occupent plus de mémoire GPU) et sollicitent davantage le cache, mais leur définition n'est pas réduite. Nous vous recommandons d'utiliser les mipmaps du moment où l'utilisation accrue de mémoire n'entraîne pas la pagination des textures en mémoire système.

 Si vos textures occupent plus de mémoire GPU que vous n'en disposez, songez à réduire la taille des textures, mais seulement après avoir envisagé de compresser les textures appropriées. Comme les textures de petite taille, les textures compressées occupent moins de mémoire et font moins appel à la pagination en mémoire système, mais elles pâtissent d'une moindre fidélité des couleurs. Si la compression ne convient pas à toutes les textures (par exemple, celles qui présentent une forte variation de couleurs sur une petite surface), ce qui dépend de leur contenu, dans bien des cas, la compression donne de meilleurs résultats en termes de qualité d'image globale que la réduction de la taille.

## <a name="remarks"></a>Remarques
 Les dimensions des textures sont réduites à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une texture source. Plus spécifiquement, les dimensions des textures sont réduites quand l'objet D3D11_TEXTURE2D_DESC passé dans `pDesc` décrit une texture utilisée dans le rendu, à savoir :

- Seul l'indicateur D3D11_BIND_SHADER_RESOURCE du membre BindFlags est défini.

- L'indicateur D3D11_RESOURCE_MISC_TILE_POOL ou D3D11_RESOURCE_MISC_TILED n'est pas défini pour le membre MiscFlags (les ressources en mosaïque ne sont pas redimensionnées).

- Le format de texture est pris en charge en tant que cible de rendu (déterminé par D3D11_FORMAT_SUPPORT_RENDER_TARGET), ce qui est nécessaire pour réduire la taille des textures. Les formats BC1, BC2 et BC3 sont aussi pris en charge, même s'ils ne sont pas pris en charge en tant que cibles de rendu.

  Si les données initiales sont fournies par l'application, cette variante met les données de texture à l'échelle appropriée avant de créer la texture. Si les données initiales sont fournies dans un format de compression de blocs tel que BC1, BC2 ou BC3, elles sont décodées, mises à l'échelle, puis réencodées avant d'être utilisées pour créer la texture plus petite. (Du fait de la nature de la compression de blocs, le processus de décodage/mise à l'échelle/encodage entraîne presque toujours une perte de qualité d'image par rapport à une texture à blocs compressés générée à partir d'une version mise à l'échelle de la texture qui n'avait pas été auparavant encodée.)

  Si les mipmaps sont activés pour la texture, la variante réduit le nombre de niveaux MIP en conséquence (un de moins pour une taille réduite de moitié ou deux de moins pour une taille réduite au quart).

## <a name="example"></a>Exemple
 Cette variante redimensionne les textures au moment de l’exécution avant l’appel à `CreateTexture2D` . Nous déconseillons cette approche pour le code de production, car les textures de taille réelle consomment plus d'espace disque et cette étape supplémentaire peut allonger sensiblement les temps de chargement dans votre application (surtout dans le cas des textures compressées, qui nécessitent des ressources de calcul importantes pour l'encodage). Nous vous recommandons plutôt de redimensionner vos textures hors connexion en utilisant un éditeur ou un processeur d'images intégré à votre pipeline de génération. Ces approches réduisent les besoins en espace disque, éliminent les surcharges au moment de l'exécution de votre application et autorisent un temps de traitement supérieur, ce qui vous permet de conserver une qualité d'image optimale lors de la réduction ou de la compression de vos textures.

## <a name="see-also"></a>Voir aussi
- [Variante de génération mipmap](mip-map-generation-variant.md)
- [Variante de compression de texture BC](bc-texture-compression-variant.md)