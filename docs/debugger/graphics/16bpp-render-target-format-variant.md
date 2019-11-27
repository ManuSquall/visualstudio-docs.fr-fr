---
title: Variante de format de cible de rendu 16 bpp | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188589"
---
# <a name="16-bpp-render-target-format-variant"></a>Variante de format cible de rendu de 16 bpp
Affecte aux pixels le format DXGI_FORMAT_B5G6R5_UNORM pour toutes les cibles de rendu et toutes les mémoires tampons d'arrière-plan.

## <a name="interpretation"></a>Interprétation
 Une cible de rendu ou une mémoire tampon d’arrière-plan utilise généralement un format 32 BPP (32 bits par pixel) comme B8G8R8A8_UNORM. les formats 32-BPP peuvent consommer une grande quantité de bande passante de mémoire. Étant donné que le format de B5G6R5_UNORM est un format de 16 bpp qui représente la moitié de la taille des formats 32-BPP, son utilisation peut réduire la pression sur la bande passante de mémoire, mais au détriment de la fidélité des couleurs.

 Si cette variante donne lieu à un net gain de performances, cela indique probablement que votre application consomme trop de bande passante de mémoire. Vous pouvez améliorer considérablement les performances, en particulier lorsque le cadre profilé avait une quantité significative de surdessin ou de fusion alpha.

Un format de cible de rendu de 16 bpp peut réduire la bande passante avec l’utilisation lorsque votre application a les conditions suivantes :
- Ne nécessite pas de reproduction haute fidélité des couleurs.
- Ne requiert pas de canal alpha.
- N’a souvent pas de dégradés lisses (qui sont susceptibles de mettre en bande des artefacts sous une fidélité des couleurs réduite).

Les autres stratégies permettant de réduire la bande passante de la mémoire sont les suivantes :
- Réduisez la quantité de surdessin ou de fusion alpha.
- Réduisez les dimensions de la mémoire tampon de trame.
- Réduisez les dimensions des ressources de texture.
- Réduisez les compressions des ressources de texture.

Comme toujours, vous devez réfléchir aux avantages et aux inconvénients qui accompagnent ces optimisations de qualité d'image.

Les applications qui font partie d’une chaîne de permutation ont un format de mémoire tampon d’arrière-plan (DXGI_FORMAT_B5G6R5_UNORM) qui ne prend pas en charge 16 bpp. Ces chaînes de permutation sont créées à l’aide de `D3D11CreateDeviceAndSwapChain` ou `IDXGIFactory::CreateSwapChain`. Pour contourner cette limitation, procédez comme suit :
1. Créez une cible de rendu de format B5G6R5_UNORM à l’aide de `CreateTexture2D` et rendez-la sur cette cible.
2. Copiez la cible de rendu dans la mémoire tampon de la chaîne d’échange en dessinant un Quad plein écran avec la cible de rendu comme texture source.
3. Appel présent sur votre chaîne de permutation.

   Si cette stratégie économise plus de bande passante que celle consommée par la copie de la cible de rendu dans la mémoire tampon de la chaîne d’échange, les performances de rendu sont améliorées.

   Les architectures GPU qui utilisent des techniques de rendu en mosaïque peuvent voir des avantages significatifs en matière de performances à l’aide d’un format de mémoire tampon de trame de 16 bpp. Cette amélioration est due au fait qu’une plus grande partie de la mémoire tampon de trame peut être contenue dans le cache de tampons de frame local de chaque mosaïque. Les architectures de rendu en mosaïque sont parfois rencontrées dans les GPU des combinés mobiles et des tablettes ; elles sont peu courantes en dehors de cette niche.

## <a name="remarks"></a>Notes
 Le format cible de rendu est réinitialisé en DXGI_FORMAT_B5G6R5_UNORM à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une cible de rendu. Plus précisément, le format est substitué quand l'objet D3D11_TEXTURE2D_DESC passé dans pDesc décrit une cible de rendu ; à savoir :

- L'indicateur D3D11_BIND_REDNER_TARGET est défini pour le membre BindFlags.

- L'indicateur D3D11_BIND_DEPTH_STENCIL est effacé pour le membre BindFlags.

- Le membre Usage a la valeur D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restrictions et limitations
 Sachant que le format B5G6R5 n'a pas de canal alpha, le contenu alpha n'est pas conservé par cette variante. Si le rendu de votre application nécessite la présence d'un canal alpha dans votre cible de rendu, il vous suffit de passer au format B5G6R5.

## <a name="example"></a>Exemple
 La variante de **format cible de rendu 16 bpp** peut être reproduite pour les cibles de rendu créées à l’aide de `CreateTexture2D` à l’aide d’un code similaire à celui-ci :

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
