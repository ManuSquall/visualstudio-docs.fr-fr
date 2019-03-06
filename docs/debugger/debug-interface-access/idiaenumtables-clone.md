---
title: IDiaEnumTables::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f9fc227983818aa1d1c91e147a5dce650844ad8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618365"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumTables** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 `ppenum`

[out] Retourne un [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) objet qui contient un doublon de l’énumérateur. Les tables ne sont pas dupliquées, uniquement l’énumérateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)