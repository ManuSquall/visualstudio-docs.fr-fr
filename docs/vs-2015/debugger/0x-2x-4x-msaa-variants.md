---
title: les variantes MSAA x-4 x-2 0 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97203b9ecc44e5aa487f7fad35b47e050ce50766
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516785"
---
# <a name="0x2x4x-msaa-variants"></a>Variantes MSAA 0x/2x/4x
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [les variantes MSAA 0 x x-4 x-2](https://docs.microsoft.com/visualstudio/debugger/graphics/0x-2x-4x-msaa-variants).  
  
Substitue les paramètres d‘anticrénelage MSSA (Multi-Sample Anti-Aliasing) sur l‘ensemble des cibles de rendu et des chaînes de permutation.  
  
## <a name="interpretation"></a>Interprétation  
 L'anticrénelage MSSA accroît la qualité visuelle en prélevant des échantillons à plusieurs endroits dans chaque pixel ; la proportion d'échantillons prélevés est proportionnelle au niveau de MSAA. Quand l'anticrénelage MSAA est désactivé, un seul échantillon est prélevé au centre du pixel. L'activation de l'anticrénelage MSAA dans votre application a un coût modeste mais palpable sur le plan des performances de rendu, mais sous certaines charges de travail ou sur certains GPU, il est possible d'en bénéficier sans pratiquement aucun impact.  
  
 Si l'anticrénelage MSAA est déjà activé dans votre application, les variantes MSAA inférieures indiquent le coût relatif en matière de performances occasionné par un niveau supérieur d'anticrénelage MSAA. En particulier, la variante MSAA 0x indique les performances relatives de votre application sans MSAA.  
  
 Si l'anticrénelage MSAA n'est pas déjà activé dans votre application, les variantes MSAA 2x et MSAA 4x indiquent le coût relatif en termes de performances de leur activation dans votre application. Si le coût est raisonnablement bas, envisagez d'activer MSAA pour améliorer la qualité d'image de votre application.  
  
> [!NOTE]
>  Il se peut que votre matériel ne prenne pas entièrement en charge MSAA pour tous les formats. Si l'une de ces variantes rencontre une limitation matérielle qu'il n'est pas possible de contourner, sa colonne dans le tableau de résumé des performances est vide et un message d'erreur est généré.  
  
## <a name="remarks"></a>Notes  
 Ces variantes substituent le nombre d'échantillons et les arguments de qualité d'échantillon dans les appels à `ID3DDevice::CreateTexture2D`, qui sont chargés de créer des cibles de rendu. Plus précisément, ces paramètres sont substitués dans les cas suivants :  
  
-   L'objet `D3D11_TEXTURE2D_DESC` passé dans `pDesc` décrit une cible de rendu, à savoir :  
  
    -   L'indicateur D3D11_BIND_TARGET ou D3D11_BIND_DEPTH_STENCIL est défini pour le membre BindFlags.  
  
    -   Le membre Usage a la valeur D3D11_USAGE_DEFAULT.  
  
    -   Le membre CPUAccessFlags a la valeur 0.  
  
    -   Le membre MipLevels a la valeur 1.  
  
-   L'appareil prend en charge le nombre d'échantillons demandé (0, 2 ou 4) et la qualité d'échantillon (0) pour le format cible de rendu demandé (membre D3D11_TEXTURE2D_DESC::Format), ce qui est déterminé par `ID3D11Device::CheckMultisampleQualityLevels`.  
  
 Si les indicateurs D3D_BIND_SHADER_RESOUCE ou D3D11_BIND_UNORDERED_ACCESS sont définis pour le membre D3D11_TEXTURE2D_DESC::BindFlags, deux versions de la texture sont créées : dans la première, ces indicateurs sont effacés pour une utilisation en tant que cible de rendu ; dans l'autre, qui est une texture non MSAA, ces indicateurs sont laissés en l'état pour faire office de mémoire tampon de résolution pour la première version. Cela est nécessaire, car l'utilisation d'une texture MSAA en tant que ressource de nuanceur ou dans le cadre d'un accès arbitraire a peu de chances d'être valide. Par exemple, un nuanceur agissant sur cette texture générerait des résultats incorrects, car il s'attendrait à une texture non MSAA. Si la variante a créé la texture non MSAA secondaire, chaque fois que la cible de rendu MSAA est détachée du contexte de l'appareil, son contenu est résolu en texture non MSAA. De la même manière, chaque fois que la cible de rendu MSAA doit être liée en tant que ressource de nuanceur ou qu'elle est utilisée dans une vue de l'accès arbitraire, la texture non MSAA résolue est liée.  
  
 De même, ces variantes substituent les paramètres MSAA sur toutes les chaînes de permutation créées à l'aide de `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition` et `ID3D11CreateDeviceAndSwapChain`.  
  
 L'effet concret de ces modifications est que l'ensemble du rendu se produit au niveau d'une cible de rendu MSAA, mais si votre application utilise l'une de ces cibles de rendu ou mémoires tampons de chaîne de permutation comme vue de la ressource de nuanceur ou vue de l'accès arbitraire, les données sont échantillonnées à partir de la copie non MSAA résolue de la cible de rendu.  
  
## <a name="restrictions-and-limitations"></a>Restrictions et limitations  
 Dans Direct3D11, les textures MSAA sont soumises à davantage de restrictions que les textures non MSAA. Par exemple, vous ne pouvez pas appeler `ID3D11DeviceContext::UpdateSubresource` sur une texture MSAA, et l'appel de `ID3D11DeviceContext::CopySubresourceRegion` échoue si le nombre d'échantillons et la qualité d'échantillon de la ressource source et de la ressource de destination ne correspondent pas, ce qui peut se produire quand cette variante substitue les paramètres MSAA d'une ressource mais pas de l'autre.  
  
 Quand le lecture détecte ce type de conflit, elle fait son possible pour répliquer le comportement visé, mais le résultat n'est pas garanti. Bien qu'il soit rare que cela affecte les performances de ces variantes ou que leur impact en soit dissimulé, cela est possible (par exemple, quand le contrôle de flux dans un nuanceur de pixels est déterminé par le contenu précis d'une texture), car le contenu de la texture répliquée risque de ne pas être identique.  
  
## <a name="example"></a>Exemple  
 Ces variantes peuvent être reproduites pour les cibles de rendu créées à l'aide de `ID3D11Device::CreateTexture2D` avec un code similaire à celui-ci :  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Exemple  
 Ou bien, pour le chaînes de permutation créées à l'aide de IDXGISwapChain::CreateSwapChain ou D3D11CreateDeviceAndSwapChain avec un code similaire à celui-ci :  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```



