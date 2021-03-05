---
description: Crée un énumérateur qui contient le même état d’énumération que l’énumérateur de tables en cours.
title: IDiaEnumTables::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 410e02ab0a7a914c06b09b97a10fe3e2f3e3c630
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157895"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumTables** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 `ppenum`

à Retourne un objet [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) qui contient un doublon de l’énumérateur. Les tables ne sont pas dupliquées, mais uniquement l’énumérateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
