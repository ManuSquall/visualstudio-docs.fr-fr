---
title: Variante de taille Viewport 1 x 1 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5280ed07d1799346b173ccac0f0186cd2bdca992
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777602"
---
# <a name="1x1-viewport-size-variant"></a>Variante de taille Viewport 1x1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Réduit les dimensions de la fenêtre d'affichage sur toutes les cibles de rendu à 1x1 pixels.  
  
## <a name="interpretation"></a>Interprétation  
 Une fenêtre d'affichage plus petite a pour effet de réduire le nombre de pixels à ombrer, mais cela ne réduit pas le nombre de sommets à traiter. Le fait de définir les dimensions de la fenêtre d'affichage à 1x1 pixels a pour effet d'éliminer en quelque sorte l'ombrage de pixels de votre application.  
  
 Si cette variante donne lieu à un net gain de performances, cela peut indiquer que votre application consomme un taux de remplissage trop important. Cela peut indiquer que la résolution que vous avez choisie est trop élevé pour la plateforme cible ou que votre application passe beaucoup de temps à ombrer des pixels qui sont ensuite remplacés (superposition). Ce résultat suggère que la diminution de la taille de votre tampon de trame ou la réduction du nombre de superpositions aura pour effet d'améliorer les performances de votre application.  
  
## <a name="remarks"></a>Notes  
 Les dimensions de la fenêtre d'affichage sont réinitialisées à 1x1 pixels après chaque appel à `ID3D11DeviceContext::OMSetRenderTargets` ou `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Exemple  
 Cette variante peut être reproduite avec un code similaire à celui-ci :  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```



