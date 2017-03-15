---
title: "PDB_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PDB_TYPE"
helpviewer_keywords: 
  - "Structure PDB_TYPE"
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PDB_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette structure spécifie des informations sur un type de champ pris d'un symbole PDB.  
  
## Syntaxe  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```c#  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### Paramètres  
 ulAppDomainID  
 ID de l'application à partir de laquelle le symbole a eu lieu.  Cela est utilisé pour identifier une instance de l'application.  
  
 guidModule  
 GUID du module qui contient ce champ.  
  
 symid  
 L'ID du symbole qui correspond à ce champ.  
  
## Notes  
 Cette structure apparaît dans le cadre de l'union dans la structure de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) lorsque le champ d' `dwKind` de la structure d' `TYPE_INFO` est défini à `TYPE_KIND_PDB` \(une valeur de l'énumération de [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) \).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)