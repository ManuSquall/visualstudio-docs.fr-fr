---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est une interface d'extension implémentée par les implémenteurs d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) .  Il permet à l'implémenteur pour obtenir des informations sur l'environnement du processus de débogage.  
  
## Syntaxe  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Implémentez cette interface pour obtenir des informations sur l'environnement d'exécution d'un processus de débogage.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProcessQueryProperties`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[QueryProperty](../Topic/IDebugProcessQueryProperties::QueryProperty.md)|requêtes pour une valeur de propriété.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Requêtes pour les valeurs de propriété.|  
  
## Notes  
 cette interface est rarement implémentée.  
  
## Configuration requise  
 en\-tête : Portpriv.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)