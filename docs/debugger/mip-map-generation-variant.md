---
title: "Variante de g&#233;n&#233;ration mipmap | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Variante de g&#233;n&#233;ration mipmap
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Active les mipmaps sur les textures qui ne sont pas des cibles de rendu.  
  
## Interprétation  
 Les mipmaps servent principalement à éliminer les artefacts de crénelage dans les textures en cours de minimisation en précalculant des versions plus petites de la texture.  Bien que ces textures supplémentaires consomment de la mémoire GPU \(près de 33 % de plus que la texture d'origine\), elles se montrent aussi plus efficaces, car leur surface d'exposition s'intègre mieux dans le cache de texture GPU et son contenu profite d'une plus grande utilisation.  
  
 Pour les scènes 3D, les mipmaps sont recommandés quand la mémoire disponible permet de stocker les textures supplémentaires, car ils améliorent les performances de rendu et la qualité d'image.  
  
 Si cette variante donne lieu à un gain de performances sensible, cela indique que vous utilisez des textures sans avoir activé les mipmaps et que donc vous ne tirez pas le meilleur parti du cache de texture.  
  
## Notes  
 La génération de mipmaps est forcée à chaque appel à `ID3D11Device::CreateTexture2D`, qui est chargé de créer une texture source.  Plus spécifiquement, la génération de mipmaps est forcée quand l'objet D3D11\_TEXTUR2D\_DESC passé dans `pDesc` décrit une ressource de nuanceur inchangé, à savoir :  
  
-   Seul l'indicateur D3D11\_BIND\_SHADER\_RESOURCE du membre BindFlags est défini.  
  
-   Le membre Usage a la valeur D3D11\_USAGE\_DEFAULT ou D3D11\_USAGE\_IMMUTABLE.  
  
-   Le membre CPUAccessFlags a la valeur 0 \(aucun accès à l'UC\).  
  
-   Le membre Count du membre SampleDesc a la valeur 1 \(pas d'anticrénelage MSAA \(Multi\-Sample Anti\-Aliasing\)\).  
  
-   Le membre MipLevels a la valeur 1 \(absence de mipmaps\).  
  
 Quand les données initiales sont fournies par l'application, la format de texture doit prendre en charge la génération automatique de mipmaps \(déterminé par D3D11\_FORMAT\_SUPPORT\_MIP\_AUTOGEN\), sauf si le format est BC1, BC2 ou BC3 ; à défaut, la texture n'est pas modifiée et aucun mipmap n'est généré au moment où les données sont fournies.  
  
 Si des mipmaps ont été générés automatiquement pour une texture, les appels à `ID3D11Device::CreateShaderResourceView` sont modifiés pendant la lecture pour utiliser la chaîne MIP lors de l'échantillonnage de texture.  
  
## Exemple  
 La variante **Génération mipmap** peut être reproduite avec un code similaire à celui\-ci :  
  
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
  
 Pour créer une texture contenant une chaîne MIP complète, affectez à `D3D11_TEXTURE2D_DESC::MipLevels` la valeur 0.  Le nombre de niveaux MIP dans une chaîne MIP complète est de floor\(log2\(n\) \+ 1\), n étant la plus grande dimension de la texture.  
  
 Rappelez\-vous qu'au moment de fournir les données initiales à `CreateTexture2D`, vous devez fournir un objet D3D11\_SUBRESOURCE\_DATA pour chaque niveau MIP.  
  
> [!NOTE]
>  Si vous voulez fournir votre propre contenu de niveau MIP au lieu de le générer automatiquement, vous devez créer vos textures à l'aide d'un éditeur d'image qui prend en charge les textures mipmappées, puis charger le fichier et passer les niveaux MIP à `CreateTexture2D`.  
  
## Voir aussi  
 [Variante de dimensions de la texture moitié\/un quart](../debugger/half-quarter-texture-dimensions-variant.md)