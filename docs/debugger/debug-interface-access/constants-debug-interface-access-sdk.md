---
title: Constantes (Debug Interface Access SDK) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b6533b1036087dc8d0cdfe59b653774d781f55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="constants-debug-interface-access-sdk"></a>Constantes (Kit de développement logiciel Debug Interface Access)
Ces constantes de chaîne peuvent être utilisées pour identifier les différentes sections d’un fichier de base de données (PDB) de débogage programme via le SDK DIA.  
  
## <a name="constants"></a>Constantes  
 Les éléments suivants sont déclarés en tant que les macros C/C++.  
  
|Macro|Valeur|  
|-----------|-----------|  
|`DiaTable_Symbols`|L « Symboles »|  
|`DiaTable_Sections`|L « Sections »|  
|`DiaTable_SrcFiles`|L « SourceFiles »|  
|`DiaTable_LineNums`|L « LineNumbers »|  
|`DiaTable_SegMap`|L « SegmentMap »|  
|`DiaTable_Dbg`|L « Dbg »|  
|`DiaTable_InjSrc`|L « InjectedSource »|  
|`DiaTable_FrameData`|L « FrameData »|  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’utilisation de ces symboles :  
  
```C++  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dia2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)