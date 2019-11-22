---
title: 16bpp Render Target Format Variant | Microsoft Docs
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
# <a name="16-bpp-render-target-format-variant"></a>16 bpp Render Target Format Variant
Affecte aux pixels le format DXGI_FORMAT_B5G6R5_UNORM pour toutes les cibles de rendu et toutes les mémoires tampons d'arrière-plan.

## <a name="interpretation"></a>Interprétation
 A render target or back buffer typically uses a 32 bpp (32 bits per pixel) format such as B8G8R8A8_UNORM. 32-bpp formats can consume a large amount of memory bandwidth. Because the B5G6R5_UNORM format is a 16-bpp format that's half the size of 32-bpp formats, using it can relieve pressure on memory bandwidth, but at the cost of reduced color fidelity.

 Si cette variante donne lieu à un net gain de performances, cela indique probablement que votre application consomme trop de bande passante de mémoire. You can gain significant performance improvement, especially when the profiled frame had a significant amount of overdraw or alpha-blending.

A 16-bpp render target format can reduce memory band with usage when your application has the following conditions:
- Doesn't require high-fidelity color reproduction.
- Doesn't require an alpha channel.
- Doesn't often have smooth gradients (which are susceptible to banding artifacts under reduced color fidelity).

Other strategies to reduce memory bandwidth include:
- Reduce the amount of overdraw or alpha-blending.
- Reduce the dimensions of the frame buffer.
- Reduce dimensions of texture resources.
- Reduce compressions of texture resources.

Comme toujours, vous devez réfléchir aux avantages et aux inconvénients qui accompagnent ces optimisations de qualité d'image.

Applications that are a part of a swap chain have a back buffer format (DXGI_FORMAT_B5G6R5_UNORM) that doesn't support 16 bpp. These swap chains are created by using `D3D11CreateDeviceAndSwapChain` or `IDXGIFactory::CreateSwapChain`. To work around this limitation, do the following steps:
1. Create a B5G6R5_UNORM format render target by using `CreateTexture2D` and render to that target.
2. Copy the render target onto the swap-chain backbuffer by drawing a full-screen quad with the render target as your source texture.
3. Call Present on your swap chain.

   If this strategy saves more bandwidth than is consumed by copying the render target to the swap-chain backbuffer, then rendering performance is improved.

   GPU architectures that use tiled rendering techniques can see significant performance benefits by using a 16 bpp frame buffer format. This improvement is because a larger portion of the frame buffer can fit in each tile's local frame buffer cache. Les architectures de rendu en mosaïque sont parfois rencontrées dans les GPU des combinés mobiles et des tablettes ; elles sont peu courantes en dehors de cette niche.

## <a name="remarks"></a>Notes
 Le format cible de rendu est réinitialisé en DXGI_FORMAT_B5G6R5_UNORM à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une cible de rendu. Plus précisément, le format est substitué quand l'objet D3D11_TEXTURE2D_DESC passé dans pDesc décrit une cible de rendu ; à savoir :

- L'indicateur D3D11_BIND_REDNER_TARGET est défini pour le membre BindFlags.

- L'indicateur D3D11_BIND_DEPTH_STENCIL est effacé pour le membre BindFlags.

- Le membre Usage a la valeur D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Restrictions et limitations
 Sachant que le format B5G6R5 n'a pas de canal alpha, le contenu alpha n'est pas conservé par cette variante. Si le rendu de votre application nécessite la présence d'un canal alpha dans votre cible de rendu, il vous suffit de passer au format B5G6R5.

## <a name="example"></a>Exemple
 The **16 bpp Render Target Format** variant can be reproduced for render targets created by using `CreateTexture2D` by using code like this:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
