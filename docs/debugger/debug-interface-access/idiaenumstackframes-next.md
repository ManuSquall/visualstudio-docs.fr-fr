---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 77d50a6c59ea376950d8cd4653f29ba7d04f36ad
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467840"
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

dans Nombre d’éléments StackFrame dans l’énumérateur à récupérer.

 rgelt

à Tableau à remplir avec les objets [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) demandés.

 pceltFetched

à Retourne le nombre d’éléments de frame de pile dans l’énumérateur extrait.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de frames de pile. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)