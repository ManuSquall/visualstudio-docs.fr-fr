---
title: Constantes (SDK Debug Interface Access) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9e745244cd449d40aaa39fa2bac2a28183feda3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280200"
---
# <a name="constants-debug-interface-access-sdk"></a>Constantes (Kit de développement logiciel Debug Interface Access)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
```cpp#  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : dia2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)



