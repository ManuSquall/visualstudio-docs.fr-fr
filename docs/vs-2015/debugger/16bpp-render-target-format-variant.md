---
title: effectuer le rendu 16 BPP variante de Format cible | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e235fbca747cf8e7a78c7923bd2a0985cbdffc34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300328"
---
# <a name="16bpp-render-target-format-variant"></a>Variante de format cible de rendu 16 bpp
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Affecte aux pixels le format DXGI_FORMAT_B5G6R5_UNORM pour toutes les cibles de rendu et toutes les mémoires tampons d'arrière-plan.  
  
## <a name="interpretation"></a>Interprétation  
 Une cible de rendu ou une mémoire tampon d'arrière-plan utilise généralement un format 32 bpp (32 bits par pixel), tel que B8G8R8A8_UNORM. Les formats 32 bpp peuvent consommer beaucoup de bande passante de mémoire. Comme B5G6R5_UNORM est un format 16 bpp dont la taille représente la moitié de celle des formats 32 bpp, son utilisation peut soulager la bande passante de mémoire, mais au détriment de la fidélité des couleurs.  
  
 Si cette variante donne lieu à un net gain de performances, cela indique probablement que votre application consomme trop de bande passante de mémoire. Les gains de performances peuvent être particulièrement prononcés quand le frame profilé pâtit d'un grand nombre de superpositions ou contient beaucoup de simulations de transparence.  
  
 Si les types de scènes affichées par votre application ne nécessitent pas une reproduction haute fidélité des couleurs, n'exigent pas la présence d'un canal alpha dans la cible de rendu et ne contiennent pas souvent de dégradés lisses (qui sont sensibles aux effets de traîne en cas de fidélité des couleurs réduite), utilisez une cible de rendu au format 16 bpp pour réduire l'utilisation de bande passante de mémoire.  
  
 Si les scènes affichées dans votre application nécessitent une reproduction haute fidélité des couleurs ou un canal alpha ou si les dégradés lisses sont courants, envisagez d'autres stratégies pour réduire l'utilisation de bande passante de mémoire (par exemple, en réduisant le nombre de superpositions ou les simulations de transparence, en réduisant les dimensions du tampon de trame ou en faisant en sorte que les ressources de texture consomment moins de bande passante de mémoire en activant la compression ou en réduisant leurs dimensions). Comme toujours, vous devez réfléchir aux avantages et aux inconvénients qui accompagnent ces optimisations de qualité d'image.  
  
 Si vous jugez qu'une mémoire tampon d'arrière-plan de 16 bpp profiterait à votre application mais qu'elle fait partie de votre chaîne de permutation, vous devez prendre des mesures supplémentaires, car DXGI_FORMAT_B5G6R5_UNORM n'est pas un format de mémoire tampon d'arrière-plan pris en charge pour les chaînes de permutation créées à l'aide de `D3D11CreateDeviceAndSwapChain` ou `IDXGIFactory::CreateSwapChain`. Au lieu de cela, vous devez créer une cible de rendu au format B5G6R5_UNORM à l'aide de `CreateTexture2D` et axer le rendu sur cette cible. Ensuite, avant d'appeler Present dans votre chaîne de permutation, copiez la cible de rendu dans la mémoire tampon d'arrière-plan de la chaîne de permutation en traçant une quadravision en plein écran avec la cible de rendu comme texte source. Bien qu'il s'agisse d'une mesure supplémentaire appelée à consommer de la bande passante de mémoire, la plupart des opérations de rendu consommeront moins de bande passante, car elles affectent la cible de rendu 16 bpp ; si, en copiant la cible de rendu dans la mémoire tampon de la chaîne de permutation, il y a plus de bande passante épargnée que consommée, les performances de rendu s'en trouvent améliorées.  
  
 Les architectures GPU qui utilisent des techniques de rendu en mosaïque peuvent profiter considérablement de l'utilisation d'un format de tampon de trame de 16 bpp sur le plan des performances, car une plus grande partie du tampon de trame peut tenir dans le cache de tampon de trame local de chaque mosaïque. Les architectures de rendu en mosaïque sont parfois rencontrées dans les GPU des combinés mobiles et des tablettes ; elles sont peu courantes en dehors de cette niche.  
  
## <a name="remarks"></a>Notes  
 Le format cible de rendu est réinitialisé en DXGI_FORMAT_B5G6R5_UNORM à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une cible de rendu. Plus précisément, le format est substitué quand l'objet D3D11_TEXTURE2D_DESC passé dans pDesc décrit une cible de rendu ; à savoir :  
  
-   L'indicateur D3D11_BIND_REDNER_TARGET est défini pour le membre BindFlags.  
  
-   L'indicateur D3D11_BIND_DEPTH_STENCIL est effacé pour le membre BindFlags.  
  
-   Le membre Usage a la valeur D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Restrictions et limitations  
 Sachant que le format B5G6R5 n'a pas de canal alpha, le contenu alpha n'est pas conservé par cette variante. Si le rendu de votre application nécessite la présence d'un canal alpha dans votre cible de rendu, il vous suffit de passer au format B5G6R5.  
  
## <a name="example"></a>Exemple  
 Le **Format cible de rendu 16 BPP** variante peut être reproduite pour les cibles de rendu créées à l’aide de `CreateTexture2D` à l’aide de code similaire à celui-ci :  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```



