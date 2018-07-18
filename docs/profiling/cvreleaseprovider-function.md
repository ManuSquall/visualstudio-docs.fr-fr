---
title: CvReleaseProvider, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f968ffaa4e11953fd3321861b884e6dda1f39a3c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750075"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider, fonction
Libère le fournisseur de marqueurs. La libération du fournisseur de marqueurs n’affecte pas les séries de marqueurs précédemment créées par ce fournisseur. Les séries de marqueurs doivent être libérées séparément par un appel CvReleaseMarkerSeries. Si la libération du fournisseur échoue, une fuite de mémoire se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```C  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProvider`  
 Contexte du fournisseur. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque le fournisseur est correctement libéré, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkers.h*  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)