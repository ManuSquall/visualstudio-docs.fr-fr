---
title: Constantes (SDK Debug Interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc54e15014e05f539c115675a97690e685cb5f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852058"
---
# <a name="constants-debug-interface-access-sdk"></a>Constantes (Kit de développement logiciel Debug Interface Access)
Ces constantes de chaîne peuvent être utilisés pour identifier les différentes sections d’un fichier de base de données (PDB) de débogage de programme via le SDK DIA.  
  
## <a name="constants"></a>Constantes  
 Les éléments suivants sont déclarés en tant que macros C/C++.  
  
|Macro|Value|  
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
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces (Kit SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)