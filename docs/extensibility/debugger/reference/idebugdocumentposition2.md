---
title: "IDebugDocumentPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "Interface de IDebugDocumentPosition2"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une position abstraite dans un fichier source.  
  
## Syntaxe  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente généralement cette interface.  Un moteur \(DE\) de débogage implémente également cette interface s'il doit fournir son propre code source \(comme lorsque le De implémente l'interface d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) \).  
  
## Remarques pour les appelants  
 Cette interface est passée comme argument à [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md).  Il est également fourni dans le cadre d'une union de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) plus précisément, une structure de [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) \) qui est ensuite une partie de la structure de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , qui est utilisée en créant un point d'arrêt en attente.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugDocumentPosition2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtient le nom du fichier source contenant la position de document.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|obtient le document contenant.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|détermine si cette position est contenue dans le document donné.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|obtient la plage pour cette position de document.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)