---
title: IDiaSymbol::get_udtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1bd7e4963796858e7055667c1ae6a9557c77205
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739031"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
Récupère la variété d’un type défini par l’utilisateur (UDT).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne une valeur de l’énumération d' [énumération UdtKind](../../debugger/debug-interface-access/udtkind.md) qui spécifie le type d’un UDT : structure, Class ou Union.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [UdtKind, énumération](../../debugger/debug-interface-access/udtkind.md)