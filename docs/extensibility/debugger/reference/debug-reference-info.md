---
title: "DEBUG_REFERENCE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REFERENCE_INFO"
helpviewer_keywords: 
  - "Structure DEBUG_REFERENCE_INFO"
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit une référence.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```c#  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## Membres  
 dwFields  
 Une combinaison des indicateurs d'énumération de [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) qui spécifie quels champs sont remplis.  
  
 bstrName  
 le nom spécifié par l'utilisateur de l'objet d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  
  
 bstrType  
 Le type référence sous la forme d'une chaîne mise en forme.  
  
 bstrValue  
 La valeur de référence sous la forme d'une chaîne mise en forme  
  
 dwAttrib  
 Une combinaison des indicateurs d'énumération de [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) qui spécifie des indicateurs pour la propriété de débogage attributes.  
  
 dwRefType  
 Une valeur de l'énumération de [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md) qui indique si le type référence est fort ou faible.  
  
 m\_pReference  
 un objet d' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) qui spécifie les informations de référence.  
  
## Notes  
 Cette structure est passée à un appel à la méthode d' [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) à accomplir.  Cette structure est également retourné dans le cadre d'une liste de l'interface d' [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) qui, à son tour, est retournée à partir d'un appel à la méthode d' [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)