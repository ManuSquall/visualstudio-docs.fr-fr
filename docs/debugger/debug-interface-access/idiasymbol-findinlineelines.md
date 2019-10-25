---
title: IDiaSymbol::findInlineeLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4876c3fe5d44ae35a26da2b68765eacc01ccfba9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741233"
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

à Contient un objet `IDiaEnumLineNumbers` qui contient la liste des numéros de ligne qui sont récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)