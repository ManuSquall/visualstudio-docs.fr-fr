---
title: "IDebugEngineLaunch2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "Interface de IDebugEngineLaunch2"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilisé par un moteur de \(DE\) débogage pour démarrer et arrêter des programmes.  
  
## Syntaxe  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par un personnalisé pour savoir si elle a des spécifications particulières pour démarrer un processus qui ne peut pas être exécuté entièrement par un port personnalisé.  C'est généralement le cas lorsque le De fait partie d'un interpréteur et le processus débogué est un script : l'interpréteur doit être exécuté en premier lieu, et le script est chargé et ensuite démarré.  Un port peut lancer l'interpréteur, mais le script peut nécessiter une gestion spéciale \(qui est l'endroit où le De a un rôle\).  Cette interface est implémentée uniquement s'il existe d'uniques spécifications pour exécuter un programme qu'un port personnalisé ne peut pas traiter.  
  
## Remarques pour les appelants  
 Cette interface est appelée par le gestionnaire de débogage de \(SDM\) session si le SDM obtienne cette interface de l'interface d' [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) \(à appeler QueryInterface\).  Si cette interface peut être obtenue, le SDM sait que le du a des spécifications spéciales et appelle cette interface pour exécuter le programme au lieu d'avoir le lancement de port \-le.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugEngineLaunch2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Exécute un processus par l'intermédiaire de le De.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Les synthèses traitent l'exécution.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|détermine si un processus peut être terminé.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Terminer un processus.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)