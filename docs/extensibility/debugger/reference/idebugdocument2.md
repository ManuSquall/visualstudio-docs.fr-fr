---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "Interface de IDebugDocument2"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un document source.  
  
## Syntaxe  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implémente généralement cette interface.  Un moteur \(DE\) de débogage peut également implémenter cette interface lorsqu'il doit fournir le code source et la source n'existe pas sur le disque.  Dans ce cas, le De implémente également les interfaces d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) et d' [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) , ainsi que certaines méthodes supplémentaires sur les interfaces d' [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) et d' [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .  
  
## Remarques pour les appelants  
 Les méthodes sur `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, et les interfaces d' `IDebugActivateDocumentEvent2` retournent cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugDocument2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtient le nom du document dans un plusieurs formes.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|obtient l'identificateur de classe du document.|  
  
## Notes  
 Cette interface est implémentée uniquement lorsque le De fournit le code source.  Par exemple, lorsque vous déboguez un script sur une page HTML, fournit de code source car la source est téléchargée ou générée dynamiquement et n'existe pas comme un fichier sur disque.  Lors de le débogage de langages traditionnels, tels que C\+\+, cette interface n'a pas besoin d'être implémentée.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)   
 [GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)