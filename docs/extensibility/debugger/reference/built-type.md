---
title: "BUILT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "Structure BUILT_TYPE"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure spécifie des informations sur un type de champ pris des métadonnées.  
  
## Syntaxe  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### Paramètres  
 ulAppDomainID  
 ID de l'application à partir de laquelle le symbole a eu lieu.  Cela est utilisé pour identifier une instance de l'application.  
  
 guidModule  
 GUID du module qui contient ce champ.  
  
 pUnderlyingField  
 Un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) identifiant le champ sous\-jacent associé à ce champ créé.  
  
## Notes  
 Cette structure apparaît dans le cadre de l'union dans la structure de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) lorsque le champ d' `dwKind` de la structure d' `TYPE_INFO` est défini à `TYPE_KIND_BUILT` \(une valeur de l'énumération de [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) \).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)