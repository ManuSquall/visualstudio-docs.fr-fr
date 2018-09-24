---
title: marker_series::marker_series, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbc397fa88c722f6a7f16ac92f4388525073c0fa
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845621"
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkersobj.h*  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [marker_series, classe](../profiling/marker-series-class.md)