---
title: IDiaSession::findSymbolByVAEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de381b67e84233b0ba4f7a6e3aaa6a4df0c93a67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465537"
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
Récupère un type de symbole spécifié qui contient ou est le plus proche de, une adresse virtuelle spécifiée (VA) et un décalage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findSymbolByVAEx ( 
   ULONGLONG    va,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Paramètres
 `va`

dans Spécifie le VA.

 `symtag`

dans Type de symbole à trouver. Les valeurs sont extraites de l’énumération d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .

 `ppSymbol`

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole récupéré.

 `displacement`

à Retourne une valeur qui spécifie un offset à partir de l’adresse virtuelle fournie par `va` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)