---
title: CvReleaseProvider, fonction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d5e611c2a964fcbb78a387a09989436e672ecd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551232"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Libère le fournisseur de marqueurs. La libération du fournisseur de marqueurs n’affecte pas les séries de marqueurs précédemment créées par ce fournisseur. Les séries de marqueurs doivent être libérées séparément par un appel CvReleaseMarkerSeries. Si la libération du fournisseur échoue, une fuite de mémoire se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProvider`  
 Contexte du fournisseur. Ne peut pas avoir la valeur NULL.  
  
## <a name="return-value"></a>Valeur renvoyée  
 S_OK lorsque le fournisseur est correctement libéré, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkers.h  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)
