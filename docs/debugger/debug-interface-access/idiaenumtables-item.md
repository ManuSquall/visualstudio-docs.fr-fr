---
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743751"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Récupère une table au moyen d’un index ou d’un nom.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Paramètres
 `index`

dans Index ou nom du [IDiaTable](../../debugger/debug-interface-access/idiatable.md) à récupérer. Si un variant entier est utilisé, il doit être compris entre 0 et `count`-1, où `count` est retourné par la méthode [IDiaEnumTables :: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

à Retourne un objet [IDiaTable](../../debugger/debug-interface-access/idiatable.md) représentant la table souhaitée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si un variant de chaîne est spécifié, la chaîne désigne une table particulière. Le nom doit correspondre à l’un des noms de table définis dans [constantes (kit de développement logiciel de debug interface Access)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Exemple

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Constantes (Kit de développement logiciel Debug Interface Access)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)