---
description: Récupère un nombre spécifié de contributions de section dans la séquence d’énumération.
title: IDiaEnumSectionContribs::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d6e33d1c56b1dd2501af2a84af8fbeef5a2831e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159320"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Récupère un nombre spécifié de contributions de section dans la séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de contributions de section dans l’énumérateur à récupérer.

 rgelt

à Tableau qui doit être rempli avec les objets [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) qui représentent les contributions de section souhaitées.

 pceltFetched

à Retourne le nombre de contributions de section dans l’énumérateur extrait.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de contributions de section. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
