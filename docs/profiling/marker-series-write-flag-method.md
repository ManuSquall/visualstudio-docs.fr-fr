---
description: Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.
title: marker_series::write_flag, méthode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersojb/Concurrency, diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5223c466674ba0d7d623cc33a3989d359bbabea2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223886"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series::write_flag, méthode
Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
void write_flag(
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Paramètres
 `_Format` Chaîne de mise en forme composite contenant du texte associé à zéro, un ou plusieurs éléments de mise en forme qui correspondent aux objets de la liste d’arguments.

 `_Importance` Niveau d’importance.

 `_Category` Catégorie.

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms** : Concurrency::diagnostic

## <a name="see-also"></a>Voir aussi
- [classe marker_series](../profiling/marker-series-class.md)
