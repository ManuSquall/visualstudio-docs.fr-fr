---
title: IDiaSymbol::findInlineeLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eefbfd9d0d19269c96699a624400fb77c83c9fb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863689"
---
# <a name="idiasymbolfindinlineelines"></a>IDiaSymbol::findInlineeLines
Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, dans ce symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLines ( 
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `ppResult`

à Contient un `IDiaEnumLineNumbers` objet qui contient la liste des numéros de ligne qui sont récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)