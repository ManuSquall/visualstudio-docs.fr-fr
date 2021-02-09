---
title: marker_series::is_enabled, méthode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e68ec76737308d9bc9478f4106420626389f5eeb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917730"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled, méthode
Détermine si une session a activé le fournisseur.

## <a name="syntax"></a>Syntaxe

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Paramètres
 `_Importance` Niveau d’importance.

 `_Category` Catégorie.

## <a name="return-value"></a>Valeur retournée

## <a name="requirements"></a>Configuration requise
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms** : Concurrency::diagnostic

## <a name="see-also"></a>Voir aussi
- [classe marker_series](../profiling/marker-series-class.md)