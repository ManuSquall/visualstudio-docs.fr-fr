---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833300"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Récupère un nombre spécifié d’éléments de frame de pile à partir de la séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

[in] Le nombre d’éléments de stackframe dans l’énumérateur à récupérer.

 rgelt

[out] Un tableau qui doit être renseigné avec demandé [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objets.

 pceltFetched

[out] Retourne le nombre de pile des éléments de cadre dans l’énumérateur extraite.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il en existe aucun frame de pile plus. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)