---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider, fonction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 036eba6fd1c25b475b703f49e1841c647d5fbd9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962168"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider, fonction
Crée des séries de marqueurs par défaut d’un fournisseur par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```C  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppProvider`  
 Adresse de variable objet de fournisseur. L’adresse ne peut pas être Null et la variable peut avoir n’importe quelle valeur.  
  
 `ppMarkerSeries`  
 Adresse de variable objet de série de marqueurs. L’adresse ne peut pas être Null et la variable peut avoir n’importe quelle valeur.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque le fournisseur et la série de marqueurs sont tous deux correctement créés, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** *cvmarkers.h*  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)