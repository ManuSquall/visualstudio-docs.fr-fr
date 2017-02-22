---
title: "IDebugErrorEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2"
helpviewer_keywords: 
  - "Interface de IDebugErrorEvent2"
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface spécifie un message d'erreur à signaler à l'utilisateur.  
  
## Syntaxe  
  
```  
IDebugErrorEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour enregistrer les erreurs en tant que messages explicites.  l'interface d' [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface.  Le SDM utilise [QueryInterface](/visual-cpp/atl/queryinterface) pour accéder à l'interface d' `IDebugEvent2` .  
  
## Remarques pour les appelants  
 Le du crée et envoie cet objet événement pour signaler une erreur.  L'événement est envoyé à l'aide de la fonction de rappel d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu'elle s'est attachée le programme débogué.  
  
## méthodes en commande de Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|`GetErrorMessage`|Retourne une erreur en tant que chaîne explicite.|  
  
## Notes  
 Si le moteur de débogage rencontre une erreur, il peut utiliser cette interface pour enregistrer le message via Visual Studio à l'utilisateur.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)