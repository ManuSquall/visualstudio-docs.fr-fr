---
title: "dwTYPE_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "dwTYPE_KIND (énumération)"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie comment interpréter le type d'un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Syntaxe  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### Paramètres  
 TYPE\_KIND\_METADATA  
 L'union de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) doit être interprétée comme structure de [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) .  
  
 TYPE\_KIND\_PDB  
 L'union d' `TYPE_INFO` doit être interprétée comme structure de [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .  
  
 TYPE\_KIND\_BUILT  
 L'union d' `TYPE_INFO` doit être interprétée comme structure de [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) .  
  
## Notes  
 Les valeurs de cette énumération s'affichent dans le champ d' `dwKind` de la structure de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) et sont utilisées pour déterminer comment interpréter le union d' `type` .  la structure d' `TYPE_INFO` est retournée par un appel à la méthode d' [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) .  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)