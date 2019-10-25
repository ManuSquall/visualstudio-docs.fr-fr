---
title: IDiaSymbol::findInlineeLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de092109282506747606799b45b89059bf41fd8a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741187"
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, dans ce symbole, dans l’adresse virtuelle (VA) spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLinesByVA ( 
   ULONGLONG             va,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `va`

dans Spécifie l’adresse en tant que VA.

 `length`

dans Spécifie la plage d’adresses, en nombre d’octets, à couvrir avec cette requête.

 `ppResult`

à Contient un objet `IDiaEnumLineNumbers` qui contient la liste des numéros de ligne qui sont récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)