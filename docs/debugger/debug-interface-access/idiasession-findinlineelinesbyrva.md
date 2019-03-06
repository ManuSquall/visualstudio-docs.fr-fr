---
title: IDiaSession::findInlineeLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 900680fe58ab5061d3f8cca07fa1906cf34f7e5b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642259"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Récupère une énumération qui permet au client d’effectuer une itération dans les informations de numéro de ligne de toutes les fonctions qui sont inline, directement ou indirectement, par le symbole parent spécifié et est contenue dans l’adresse virtuelle relative (RVA) spécifié.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

[in] Un `IDiaSymbol` objet représentant le parent.

 `rva`

[in] Spécifie l’adresse comme une RVA.

 `length`

[in] Spécifie la plage d’adresses, en octets, pour couvrir cette requête.

 `ppResult`

[out] Contient un `IDiaEnumLineNumbers` objet qui contient la liste des numéros de ligne qui sont récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)