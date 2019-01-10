---
title: effectuer le rendu 16 BPP variante de Format cible | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab58cbcd6644d540b7db2efb1cad59e5d80f8530
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986659"
---
# <a name="16-bpp-render-target-format-variant"></a>Restituer variante de Format cible de 16 bpp
Affecte aux pixels le format DXGI_FORMAT_B5G6R5_UNORM pour toutes les cibles de rendu et toutes les mémoires tampons d'arrière-plan.  
  
## <a name="interpretation"></a>Interprétation  
 Une cible de rendu ou de la mémoire tampon d’arrière-plan utilise généralement un format 32 bpp (32 bits par pixel) tel que B8G8R8A8_UNORM. les formats 32 bpp peuvent consommer une grande quantité de bande passante de mémoire. Étant donné que le format B5G6R5_UNORM est un format de 16 bits par pixel qui est la moitié des formats de 32 bpp, son utilisation peut soulager la pression sur la bande passante de mémoire, mais au détriment de la fidélité des couleurs réduite.  
  
 Si cette variante donne lieu à un net gain de performances, cela indique probablement que votre application consomme trop de bande passante de mémoire. Vous pouvez obtenir l’amélioration significative des performances, en particulier lorsque le frame profilé avait une quantité importante de superpositions ou mélange alpha.

Un format de cible de rendu 16 bits par pixel peut réduire la bande de mémoire avec utilisation lorsque votre application a les conditions suivantes :
- Ne nécessite pas une reproduction haute fidélité des couleurs.
- Ne nécessite pas un canal alpha.
- Ofent ne dispose pas des dégradés lisses (qui sont vulnérables aux artefacts répartis sous la fidélité des couleurs réduite).

Autres stratégies pour réduire la bande passante de mémoire sont les suivantes :
- Réduire la quantité de superpositions ou mélange alpha.
- Réduire les dimensions de la mémoire tampon de trame.
- Réduisez les dimensions de ressources de texture.
- Réduire les compressions de ressources de texture.
 
Comme toujours, vous devez réfléchir aux avantages et aux inconvénients qui accompagnent ces optimisations de qualité d'image.  

Les applications qui font partie d’une chaîne de permutation ont un format de mémoire tampon d’arrière-plan (DXGI_FORMAT_B5G6R5_UNORM) qui ne prend pas en charge 16 bpp. Ces chaînes de permutation sont créés à l’aide de `D3D11CreateDeviceAndSwapChain` ou `IDXGIFactory::CreateSwapChain`. Pour contourner cette limitation, procédez comme suit :
1. Créer une cible de rendu de format B5G6R5_UNORM à l’aide de `CreateTexture2D` et à la cible de rendu. 
2. Copiez la cible de rendu dans la chaîne de permutation quadravision en dessinant un quadruple plein écran avec la cible de rendu en tant que votre texture source.
3. Appeler Present dans votre chaîne de permutation.

   Si cette stratégie permet d’économiser davantage de bande passante que consommée en copiant la cible de rendu dans la chaîne de permutation mémoire tampon d’arrière-plan, les performances de rendu est améliorée.

   Les architectures GPU qui utilisent des techniques de rendu en mosaïque peuvent voir les avantages de performance significatifs à l’aide d’un format de mémoire tampon de trame de 16 bpp. Cette amélioration est, car une plus grande partie de la mémoire tampon de trame peut tenir dans le cache des tampons frame local de chaque mosaïque. Les architectures de rendu en mosaïque sont parfois rencontrées dans les GPU des combinés mobiles et des tablettes ; elles sont peu courantes en dehors de cette niche.  
  
## <a name="remarks"></a>Notes  
 Le format cible de rendu est réinitialisé en DXGI_FORMAT_B5G6R5_UNORM à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une cible de rendu. Plus précisément, le format est substitué quand l'objet D3D11_TEXTURE2D_DESC passé dans pDesc décrit une cible de rendu ; à savoir :  
  
-   L'indicateur D3D11_BIND_REDNER_TARGET est défini pour le membre BindFlags.  
  
-   L'indicateur D3D11_BIND_DEPTH_STENCIL est effacé pour le membre BindFlags.  
  
-   Le membre Usage a la valeur D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Restrictions et limitations  
 Sachant que le format B5G6R5 n'a pas de canal alpha, le contenu alpha n'est pas conservé par cette variante. Si le rendu de votre application nécessite la présence d'un canal alpha dans votre cible de rendu, il vous suffit de passer au format B5G6R5.  
  
## <a name="example"></a>Exemple  
 Le **16 bpp Format cible de rendu** variante peut être reproduite pour les cibles de rendu créées à l’aide de `CreateTexture2D` à l’aide de code similaire à celui-ci :  
  
```cpp
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
