---
title: marker_series::marker_series, constructeur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa010c535b984eb6a00bcb8234815f3d489b87b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939450"
---
# <a name="markerseriesmarkerseries-constructor"></a>marker_series::marker_series, constructeur
Initialise une nouvelle instance de la classe `marker_series`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `_SeriesName`  
 Nom de la série à créer.  
  
 `_ProviderGuid`  
 GUID du fournisseur de la série.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** *cvmarkersobj.h*  
  
 **Espace de noms :** Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [marker_series, classe](../profiling/marker-series-class.md)