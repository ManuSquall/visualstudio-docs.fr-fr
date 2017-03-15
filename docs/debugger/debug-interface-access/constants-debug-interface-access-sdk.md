---
title: "Constantes (Kit de d&#233;veloppement logiciel Debug&#160;Interface&#160;Access) | Microsoft Docs"
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
  - "constantes, Kit de développement DIA (SDK)"
  - "Kit de développement DIA (SDK), constantes"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Constantes (Kit de d&#233;veloppement logiciel Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ces constantes de chaîne peuvent être utilisées pour identifier de différentes sections d'un fichier de base de données de débogage du programme \(PDB\) via le diamètre Kit de développement logiciel.  
  
## Constantes  
 Ce qui suit est déclaré comme macros C\/C\+\+.  
  
|Macro|Valeur|  
|-----------|------------|  
|`DiaTable_Symbols`|l " symboles »|  
|`DiaTable_Sections`|l " sections »|  
|`DiaTable_SrcFiles`|l " SourceFiles »|  
|`DiaTable_LineNums`|l " LineNumbers »|  
|`DiaTable_SegMap`|l " SegmentMap »|  
|`DiaTable_Dbg`|l " Dbg »|  
|`DiaTable_InjSrc`|l " InjectedSource »|  
|`DiaTable_FrameData`|l " FrameData »|  
  
## Exemple  
 voici un exemple utilisant un de ces symboles :  
  
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
  
## Configuration requise  
 en\-tête : dia2.h  
  
## Voir aussi  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces \(Kit de développement logiciel Debug Interface Access\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)