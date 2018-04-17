---
title: IDiaEnumTables::Item | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fad03266d5372208996c3a665ab078e14fafe7b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Récupère un tableau au moyen d’un index ou un nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 [in] Index ou le nom de la [IDiaTable](../../debugger/debug-interface-access/idiatable.md) à récupérer. Si un Variant de type integer est utilisé, il doit être comprise entre 0 et `count`-1, où `count` est renvoyé par le [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) (méthode).  
  
 `table`  
 [out] Retourne un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objet représentant la table souhaitée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si une variante de la chaîne est spécifiée, la chaîne de noms une table particulière. Le nom doit être un des noms de table comme défini dans [(Debug Interface Access SDK) des constantes](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Exemple  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes (Kit de développement logiciel Debug Interface Access)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)