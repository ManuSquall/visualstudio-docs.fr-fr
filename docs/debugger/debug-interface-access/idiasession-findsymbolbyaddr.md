---
title: IDiaSession::findSymbolByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByAddr method
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fddf38af6f6294fd3a6fa8e129d395a66f1aa80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465572"
---
# <a name="idiasessionfindsymbolbyaddr"></a>IDiaSession::findSymbolByAddr
Récupère un type de symbole spécifié qui contient ou est le plus proche d’une adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolByAddr ( 
   DWORD        isect,
   DWORD        offset,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Paramètres
 `isect`

dans Spécifie le composant de section de l’adresse.

 `offset`

dans Spécifie le composant de décalage de l’adresse.

 `symtag`

dans Type de symbole à trouver. Les valeurs sont extraites de l’énumération d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .

 `ppSymbol`

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole récupéré.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)