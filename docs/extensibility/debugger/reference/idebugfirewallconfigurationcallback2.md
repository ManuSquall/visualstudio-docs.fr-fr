---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugFirewallConfigurationCallback2"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Active un moteur de débogage qui utilise DCOM pour indiquer à [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur pour garantir que le pare\-feu ne se bloque pas le débogage distant.  
  
## Syntaxe  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Implémentée par l'objet de port du gestionnaire de débogage de session.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugFirewallConfigurationCallback2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Demande que le débogage distant de bloc de pare\-feu pas.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll