---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "Interface de IDebugDocumentTextEvents2"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est utilisée pour notifier Visual Studio sur les modifications apportées au document source fournies par le moteur de débogage.  
  
## Syntaxe  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface pour prendre en charge apporter des modifications au code source.  Cette interface est généralement implémenté sur le même objet qui implémente l'interface d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## Remarques pour les appelants  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] reçoit cette interface via un appel à la méthode d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> .  L'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> dérive d'un appel à la méthode d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> .  l'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> est obtenue en appelant la méthode de [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface d' [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugDocumentTextEvents2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|indique que le document entier a été détruit.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|informe le package de débogage que le texte a été inséré dans le document.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|informe le package de débogage que le texte a été supprimé du document.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|informe le package de débogage que le texte a été remplacé dans le document.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Informe le package de débogage que des attributs de texte ont été mis à jour dans le document.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Informe le récepteur de l'événement que les attributs de document a été mis à jour.|  
  
## Notes  
 Seuls les moteurs de débogage qui fournissent leurs propres documents tireraient parti de l'interface d' `IDebugDocumentTextEvent2` .  Un exemple de cette séquence est un moteur de débogage de script.  Il est probable que interpréter les scripts, il peut générer un nouveau code source qui n'est pas présent dans un fichier sur disque et est connu uniquement du De.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)