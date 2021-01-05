---
title: Variante de taille de fenêtre d’affichage 1x1 | Microsoft Docs
description: Appliquez la variante de taille de la fenêtre d’affichage 1x1 pour réduire les dimensions de la fenêtre d’affichage de toutes les cibles de rendu à 1x1 pixels.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1041f3a8016500a6e1f217849654d9710a508d8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726486"
---
# <a name="1x1-viewport-size-variant"></a>Variante de taille Viewport 1x1
Réduit les dimensions de la fenêtre d'affichage sur toutes les cibles de rendu à 1x1 pixels.

## <a name="interpretation"></a>Interprétation
 Une fenêtre d’affichage plus petite réduit le nombre de pixels à ombrer. Toutefois, une fenêtre d’affichage plus petite ne réduit pas le nombre de vertex que vous devez traiter. Le fait de définir les dimensions de la fenêtre d'affichage à 1x1 pixels a pour effet d'éliminer en quelque sorte l'ombrage de pixels de votre application.

 Si cette variante présente un gain de performances élevé, cela peut indiquer que votre application consomme trop de taux de remplissage. En outre, votre résolution peut être trop élevée pour la plateforme cible, ou votre application peut passer des pixels de temps d’ombrage significatifs qui sont remplacés par la suite, également connus sous le titre de *surdessin*. Une mémoire tampon de trame plus petite ou la réduction de la quantité de surdessin améliorera les performances de votre application.

## <a name="remarks"></a>Remarques
 Les dimensions de la fenêtre d'affichage sont réinitialisées à 1x1 pixels après chaque appel à `ID3D11DeviceContext::OMSetRenderTargets` ou `ID3D11DeviceContext::RSSetViewports`.

## <a name="example"></a>Exemple
 Cette variante peut être reproduite avec le code suivant :

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
