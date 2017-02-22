---
title: "DEBUG_CUSTOM_VIEWER | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_CUSTOM_VIEWER"
helpviewer_keywords: 
  - "Structure DEBUG_CUSTOM_VIEWER"
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_CUSTOM_VIEWER
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

une structure qui identifie une visionneuse ou un visualiseur personnalisée de type.  
  
## Syntaxe  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```c#  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## Membres  
 dwID  
 Un ID pour distinguer plusieurs visionneuses ou visualiseurs implémentés par un `GUID`.  
  
 bstrMenuName  
 Le texte qui apparaît dans le menu déroulant.  
  
 bstrDescription  
 Une description de la visionneuse ou du visualiseur personnalisée de type \(doit être une valeur NULL si elle n'est pas utilisée\).  
  
 guidLang  
 Langage de l'évaluateur d'expression de présentation.  
  
 guidVendor  
 Fournisseur de l'évaluateur d'expression de présentation.  
  
 bstrMetric  
 De sous mesures fournies par la visionneuse ou le visualiseur personnalisée `CLSID` de type est enregistré.  
  
## Notes  
 une liste de cette structure est retournée par un appel à la méthode d' [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) \(et, par à l'extension, à la méthode d' [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) \).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)