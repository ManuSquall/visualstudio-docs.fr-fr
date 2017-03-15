---
title: "IDebugDocumentContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2"
helpviewer_keywords: 
  - "IDebugDocumentContext2"
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente une position dans un document du fichier source.  
  
## Syntaxe  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface dans le cadre de son charge le débogage de niveau de code source.  En plus d'une position dans le code source, cette interface fournit des méthodes pour comparer des contextes et naviguer dans un document de code source.  
  
## Remarques pour les appelants  
 Les méthodes sur plusieurs interfaces, le plus courant les interfaces d' [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) et d' [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) , retournent cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugDocumentContext2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)|obtient le document qui contient ce contexte de document.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|obtient le nom affichable du document qui contient ce contexte de document.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Extrait une liste de tous les contextes de code associés à ce contexte de document.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Obtient la langue associé à ce contexte de document.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la plage d'instructions de fichier de ce contexte de document.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Obtient la plage source du fichier de ce contexte de document.|  
|[Comparer](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Compare ce contexte de document vers un tableau donné de contextes de document.|  
|[Recherche](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Déplace le contexte de document par un nombre donné d'instructions ou de lignes.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)