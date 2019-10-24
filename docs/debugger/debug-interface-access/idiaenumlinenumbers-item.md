---
title: IDiaEnumLineNumbers::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bba71efce68864b8737011ab7dda5cb8da3267c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744398"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Récupère un numéro de ligne au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) à récupérer. L’index se trouve dans la plage 0 à `count`-1, où `count` est retourné par la méthode [IDiaEnumLineNumbers :: get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) .

 lineNumber

à Retourne un objet [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) représentant le numéro de ligne souhaité.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)