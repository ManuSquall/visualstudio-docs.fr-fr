---
title: "IEnumDebugPorts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface énumère les ports d'un ordinateur ou d'un fournisseur de port.  
  
## Syntaxe  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour représenter une liste de ports créés par le fournisseur.  Visual Studio implémente cette interface à l'appui de son propre fournisseur de port.  
  
## Remarques pour les appelants  
 appelez [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) pour obtenir cette interface représentant une liste de ports créés par le fournisseur de port.  Appelez [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) pour obtenir cette interface représentant une liste de ports qui ont été enregistrés sur le disque.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugPorts2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Récupère un nombre spécifié de ports dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Ignore un nombre spécifié de ports dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../Topic/IEnumDebugPorts2::GetCount.md)|obtient le nombre de ports dans un énumérateur.|  
  
## Notes  
 Visual Studio utilise cette interface pour aider à remplir une liste de ports utilisés pour attacher les processus.  
  
 un moteur de débogage en général n'utilise pas cette interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)