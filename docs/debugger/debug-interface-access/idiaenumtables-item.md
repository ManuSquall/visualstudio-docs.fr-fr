---
title: IDiaEnumTables::Item | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26acf7b8f9ad54a1ef1ed25497cd408c51c745c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
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