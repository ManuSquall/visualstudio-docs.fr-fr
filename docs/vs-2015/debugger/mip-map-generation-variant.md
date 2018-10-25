---
title: Variante de génération de mipmap | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e983022764bc8a790987e3e0dc6045eea098a2ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913837"
---
# <a name="mip-map-generation-variant"></a>Variante de génération mipmap
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Active les mipmaps sur les textures qui ne sont pas des cibles de rendu.  
  
## <a name="interpretation"></a>Interprétation  
 Les mipmaps servent principalement à éliminer les artefacts de crénelage dans les textures en cours de minimisation en précalculant des versions plus petites de la texture. Bien que ces textures supplémentaires consomment de la mémoire GPU (près de 33 % de plus que la texture d'origine), elles se montrent aussi plus efficaces, car leur surface d'exposition s'intègre mieux dans le cache de texture GPU et son contenu profite d'une plus grande utilisation.  
  
 Pour les scènes 3D, les mipmaps sont recommandés quand la mémoire disponible permet de stocker les textures supplémentaires, car ils améliorent les performances de rendu et la qualité d'image.  
  
 Si cette variante donne lieu à un gain de performances sensible, cela indique que vous utilisez des textures sans avoir activé les mipmaps et que donc vous ne tirez pas le meilleur parti du cache de texture.  
  
## <a name="remarks"></a>Notes  
 La génération de mipmaps est forcée à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une texture source. Plus spécifiquement, la génération de mipmaps est forcée quand l'objet D3D11_TEXTUR2D_DESC passé dans `pDesc` décrit une ressource de nuanceur inchangé, à savoir :  
  
- Seul l'indicateur D3D11_BIND_SHADER_RESOURCE du membre BindFlags est défini.  
  
- Le membre Usage a la valeur D3D11_USAGE_DEFAULT ou D3D11_USAGE_IMMUTABLE.  
  
- Le membre CPUAccessFlags a la valeur 0 (aucun accès à l'UC).  
  
- Le membre Count du membre SampleDesc a la valeur 1 (pas d'anticrénelage MSAA (Multi-Sample Anti-Aliasing)).  
  
- Le membre MipLevels a la valeur 1 (absence de mipmaps).  
  
  Quand les données initiales sont fournies par l'application, la format de texture doit prendre en charge la génération automatique de mipmaps (déterminé par D3D11_FORMAT_SUPPORT_MIP_AUTOGEN), sauf si le format est BC1, BC2 ou BC3 ; à défaut, la texture n'est pas modifiée et aucun mipmap n'est généré au moment où les données sont fournies.  
  
  Si des mipmaps ont été générés automatiquement pour une texture, les appels à `ID3D11Device::CreateShaderResourceView` sont modifiés pendant la lecture pour utiliser la chaîne MIP lors de l'échantillonnage de texture.  
  
## <a name="example"></a>Exemple  
 Le **génération mipmap** variante peut être reproduite à l’aide de code similaire à celui-ci :  
  
```  
D3D11_TEXTURE2D_DESC texture_description;  
  
// ...  
  
texture_description.MipLevels = 0; // generate a full mipchain  
  
std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);  
  
for (auto&& mip_level : initial_data)  
{  
    // fill mip_level with the application-supplied initial data  
}  
  
d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)  
```  
  
 Pour créer une texture contenant une chaîne MIP complète, affectez à `D3D11_TEXTURE2D_DESC::MipLevels` la valeur 0. Le nombre de niveaux mip dans une chaîne mip complète est floor(log2(n) + 1), où n est la plus grande dimension de la texture.  
  
 Rappelez-vous qu'au moment de fournir les données initiales à `CreateTexture2D`, vous devez fournir un objet D3D11_SUBRESOURCE_DATA pour chaque niveau MIP.  
  
> [!NOTE]
>  Si vous voulez fournir votre propre contenu de niveau MIP au lieu de le générer automatiquement, vous devez créer vos textures à l'aide d'un éditeur d'image qui prend en charge les textures mipmappées, puis charger le fichier et passer les niveaux MIP à `CreateTexture2D`.  
  
## <a name="see-also"></a>Voir aussi  
 [Variante de dimensions de la texture moitié/un quart](../debugger/half-quarter-texture-dimensions-variant.md)



