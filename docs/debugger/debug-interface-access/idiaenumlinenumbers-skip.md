---
description: Ignore un nombre spécifié de numéros de ligne dans une séquence d’énumération.
title: IDiaEnumLineNumbers::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 051d55b901512168a8bca5cdaa71c487f791c8a8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148919"
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
Ignore un nombre spécifié de numéros de ligne dans une séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de numéros de ligne dans la séquence d’énumération à ignorer.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` s’il n’y a plus de numéros de ligne à ignorer.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
