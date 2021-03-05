---
description: Récupère le nombre de symboles.
title: IDiaEnumSymbols::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::get_Count method
ms.assetid: fdaae6d7-e67b-4262-84c9-fbae381e8297
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3859524adce48fb504c09c4b0bcacf8ac97a875
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159131"
---
# <a name="idiaenumsymbolsget_count"></a>IDiaEnumSymbols::get_Count
Récupère le nombre de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

à Retourne le nombre de symboles.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)
