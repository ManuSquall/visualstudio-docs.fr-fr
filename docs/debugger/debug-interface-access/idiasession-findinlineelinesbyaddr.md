---
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496f6b569b3ac02c625ddf18406b78fdb1687be2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742230"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Récupère une énumération qui permet à un client d’itérer au sein des informations de numéro de ligne de toutes les fonctions qui sont Inline, directement ou indirectement, par le symbole parent spécifié et qui sont contenues dans la plage d’adresses spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `parent`

dans Objet `IDiaSymbol` représentant le parent.

 `isect`

dans Spécifie le composant de section de l’adresse.

 `offset`

dans Spécifie le composant de décalage de l’adresse.

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