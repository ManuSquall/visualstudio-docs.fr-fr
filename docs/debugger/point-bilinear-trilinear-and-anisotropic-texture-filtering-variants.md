---
title: "Variantes de filtrage de texture ponctuelle, bilin&#233;aire, trilin&#233;aire et anisotropique | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Variantes de filtrage de texture ponctuelle, bilin&#233;aire, trilin&#233;aire et anisotropique
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Substitue le mode de filtrage sur les échantillonneurs de texture appropriés.  
  
## Interprétation  
 Le coût sur le plan des performances et la qualité d'image varient d'une méthode d'échantillonnage de texture à une autre.  Voici les différents modes de filtrage classés par ordre croissant de coût et de qualité visuelle :  
  
1.  Filtrage de points \(mode le plus économique, qualité visuelle inférieure\)  
  
2.  Filtrage bilinéaire  
  
3.  Filtrage trilinéaire  
  
4.  Filtrage anisotropique \(mode le plus coûteux, qualité visuelle optimale\)  
  
 Si le coût de chaque variante en termes de performances est significatif ou s'il augmente avec les modes de filtrage plus intensifs, vous pouvez mettre en balance le coût et la qualité d'image qu'ils procurent.  Selon votre évaluation, vous pouvez soit accepter de supporter un coût supplémentaire en termes de performances et bénéficier d'une meilleure qualité visuelle, soit opter pour une qualité visuelle réduite au profit d'une fréquence d'images supérieure, soit réserver les performances à d'autres processus.  
  
 Si vous trouvez que le coût en termes de performances est négligeable ou stable d'un mode de filtrage à un autre \(par exemple, quand le GPU ciblé offre une bande passante de mémoire et un débit de nuanceur généreux\), préférez le filtrage anisotropique pour accéder à une qualité d'image optimale dans votre application.  
  
## Notes  
 Ces variantes substituent les états de l'échantillonneur lors des appels à `ID3D11DeviceContext::PSSetSamplers` quand le mode de filtrage de l'échantillonneur fourni par l'application est l'un des suivants :  
  
-   `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_ANISOTROPIC`  
  
 Dans la variante **Filtrage de texture de point**, le mode de filtrage fourni par l'application est remplacé par `D3D11_FILTER_MIN_MAG_MIP_POINT` ; dans la variante **Filtrage de texture bilinéaire**, il est remplacé par `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` ; et dans la variante **Filtrage de texture trilinéaire**, il est remplacé par `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
 Dans la variante **Filtrage de texture anisotropique**, le mode de filtrage fourni par l'application est remplacé par `D3D11_FILTER_ANISOTROPIC`, et le paramètre d'anisotropie maximale est défini à 16.  
  
## Restrictions et limitations  
 Dans Direct3D, le niveau de fonctionnalité 9.1 spécifie une anisotropie maximale de 2x.  Étant donné que la variante **Filtrage de texture anisotropique** essaie d'utiliser exclusivement l'anisotropie 16x, la lecture échoue quand l'analyse des frames est exécutée sur un appareil ayant un niveau de fonctionnalité 9.1.  Les appareils actuels concernés par cette limitation sont notamment les tablettes Surface RT et Surface 2 ARM.  Cette limitation peut aussi toucher les GPU plus anciens qui peuvent encore équiper certains ordinateurs, mais ceux\-ci étant considérés comme obsolètes, ils sont de moins en moins répandus.  
  
## Exemple  
 La variante **Filtrage de texture de point** peut être reproduite avec un code similaire à celui\-ci :  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## Exemple  
 La variante **Filtrage de texture bilinéaire** peut être reproduite avec un code similaire à celui\-ci :  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## Exemple  
 La variante **Filtrage de texture trilinéaire** peut être reproduite avec un code similaire à celui\-ci :  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## Exemple  
 La variante **Filtrage de texture anisotropique** peut être reproduite avec un code similaire à celui\-ci :  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```