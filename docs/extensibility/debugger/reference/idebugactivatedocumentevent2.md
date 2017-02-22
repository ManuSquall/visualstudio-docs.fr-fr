---
title: "IDebugActivateDocumentEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugActivateDocumentEvent2"
helpviewer_keywords: 
  - "Interface de IDebugActivateDocumentEvent2"
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le moteur \(DE\) de débogage utilise cette interface pour demander un document à charger.  
  
## Syntaxe  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface lorsqu'il a besoin d'un fichier source pour être ouvert.  Cette interface est implémentée uniquement par les moteurs de débogage qui fonctionnent avec ou est une partie d'interpréteurs de scripts.  L'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface \(le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` \).  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement lorsqu'il doit faire ouvrir un fichier source.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'il est attaché au programme en cours de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugActivateDocumentEvent2`.  
  
|Méthodes|Description|  
|--------------|-----------------|  
|[GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)|Obtient le document pour vérifier.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|obtient le contexte de document qui décrit la position dans le document.|  
  
## Notes  
 Un scénario courant dans lequel cette interface est utilisée est si une erreur d'analyse se produit dans le code de script dans une page HTML, le script De envoie cette interface au SDM afin que le document avec l'erreur d'analyse puisse être affichée.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)