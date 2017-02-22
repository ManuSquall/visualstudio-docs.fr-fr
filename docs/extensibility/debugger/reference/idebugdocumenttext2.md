---
title: "IDebugDocumentText2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "Interface de IDebugDocumentText2"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un document texte.  
  
## Syntaxe  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## Remarques à l'intention des implémenteurs  
 Un moteur \(DE\) de débogage implémente cette interface lorsque le code source qu'il doit fournir le est au format de texte.  Étant donné que c'est le cas le plus courant, si un De implémente l'interface d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , il doit également implémenter l'interface de `IDebugDocumentText2` .  
  
## Remarques pour les appelants  
 Utilisez la méthode d' `QueryInterface` pour obtenir cette interface d'une interface d' `IDebugDocument2` .  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur l'interface d' `IDebugDocument2` , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|extrait la taille du texte à cette position dans le document.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|extrait le texte de la position spécifiée dans le document.|  
  
## Notes  
 un objet qui implémente cette interface doit également implémenter l'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> , qui fournit l'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> pour un objet d' [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)