---
description: 'IDiaSession :: findInlineFramesByVA récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse virtuelle spécifiée (VA).'
title: IDiaSession::findInlineFramesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c87af04b166448baeda14b276f0bf0b8ab8d6f10
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158963"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
Récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse virtuelle spécifiée (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineFramesByVA ( 
   IDiaSymbol*       parent,   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

dans `IDiaSymbol` Objet représentant le parent.

 `va`

dans Spécifie l’adresse en tant que VA.

 `ppResult`

à Contient un `IDiaEnumSymbols` objet qui contient la liste des frames récupérés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
