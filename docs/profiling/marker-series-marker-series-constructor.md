---
description: Initialise une nouvelle instance de la classe marker_series.
title: marker_series::marker_series, constructeur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88d82c78bc6126f6b3d96b77b39c729c4f452a28
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223977"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series::marker_series, constructeur
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
 `_SeriesName` Nom de la série à créer.

 `_ProviderGuid` GUID du fournisseur de la série.

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms** : Concurrency::diagnostic

## <a name="see-also"></a>Voir aussi
- [classe marker_series](../profiling/marker-series-class.md)
