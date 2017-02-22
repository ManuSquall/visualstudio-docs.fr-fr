---
title: "IDebugQueryEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "Interface de IDebugQueryEngine2"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface permet au gestionnaire de débogage de session \(SDM\) extraire une interface qui représente le moteur de débogage \(DE\).  
  
## Syntaxe  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le De implémente cette interface sur les objets qui implémentent la plupart du common DE interfaces \(telle qu' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), et [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\) afin de permettre l'accès à l'interface d' [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) du De lui\-même.  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface type de pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugQueryEngine2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetEngineInterface](../Topic/IDebugQueryEngine2::GetEngineInterface.md)|Obtient une interface personnalisée \(DE\) du moteur de débogage.|  
  
## Notes  
 Cette interface est généralement implémenté dans l'objet qui implémente l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pour prendre en charge la progression causalité\-classée présente les fonctions ; autrement dit, lorsque le débogueur effectue un pas \- à \- pas sortant d'une fonction, la fonction suivante à exécuter peut ne pas être la fonction précédente sur la pile mais une fonction dans un autre thread entièrement.  Pour une définition de « causalité », consultez [Glossaire du débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)