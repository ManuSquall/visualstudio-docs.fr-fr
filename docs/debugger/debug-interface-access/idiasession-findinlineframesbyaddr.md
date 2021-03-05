---
description: 'IDiaSession :: findInlineFramesByAddr récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse donnée.'
title: IDiaSession::findInlineFramesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b063828522a0ab1579b7ade1d5f780b01598e96f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157104"
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
Récupère une énumération qui permet à un client d’itérer au sein de tous les frames insérés sur une adresse donnée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineFramesByAddr ( 
   IDiaSymbol*       parent,   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

dans `IDiaSymbol` Objet représentant le parent.

 `isect`

dans Spécifie le composant de section de l’adresse.

 `offset`

dans Spécifie le composant de décalage de l’adresse.

 `ppResult`

à Contient un `IDiaEnumSymbols` objet qui contient la liste des frames récupérés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
