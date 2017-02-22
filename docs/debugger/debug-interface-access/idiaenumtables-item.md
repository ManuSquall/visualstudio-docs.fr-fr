---
title: "IDiaEnumTables::Item | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumTables::Item (méthode)"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un tableau à l'aide d'un index ou d'une étiquette.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### Paramètres  
 `index`  
 \[in\]  Indexer ou nom d' [IDiaTable](../../debugger/debug-interface-access/idiatable.md) à récupérer.  Si une variante entière est utilisée, elle doit être comprise entre 0 et `count`\-1, où `count` est le retourné par la méthode d' [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .  
  
 `table`  
 \[out\]  Retourne un objet d' [IDiaTable](../../debugger/debug-interface-access/idiatable.md) représentant la table voulue.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Si une variante de chaîne est spécifiée, les noms de chaîne une table spécifique.  Le nom doit être l'un des noms de tables comme défini dans [Constantes \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## Exemple  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## Voir aussi  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)