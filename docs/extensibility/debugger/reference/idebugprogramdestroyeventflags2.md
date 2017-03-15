---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugProgramDestroyEventFlags2"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permet à un moteur de débogage pour remplacer le comportement par défaut de  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]interface utilisateur lorsque vous terminez une session de débogage.  
  
## Syntaxe  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par les moteurs de débogage.  Elle est utile pour les hôtes qui peuvent créer et détruire des programmes multiples pendant la durée de vie d'un processus.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugProgramDestroyEventFlags2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Récupère le programme détruisent des balises.|  
  
## Notes  
 Le comportement par défaut de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface utilisateur est pour revenir aux programmes de mode Design après tout a envoyé un programme destroy l'événement.  cette interface permet à un moteur de débogage pour modifier ce comportement.  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll