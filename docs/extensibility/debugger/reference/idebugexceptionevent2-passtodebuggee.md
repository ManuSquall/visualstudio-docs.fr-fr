---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie si l'exception doit être passée dans le programme débogué lorsque l'exécution se poursuit, ou si l'exception est ignorée.  
  
## Syntaxe  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### Paramètres  
 `fPass`  
 \[in\]  Une valeur différente de zéro \(`TRUE`\) si l'exception est passée dans le programme débogué lorsque l'exécution se poursuit, ou zéro \(`FALSE`\) si l'exception est ignorée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Appeler cette méthode ne provoque pas réellement de code à exécuter dans le programme débogué.  l'appel est simplement de définir l'état pour l'exécution de code suivante.  Par exemple, les appels à la méthode d' [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) peuvent retourner `S_OK` avec [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md). champ d'`dwState` défini à `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 L'IDE peut recevoir l'événement d' [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) et appeler la méthode d' [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md) .  Le moteur de \(DE\) débogage doit avoir un comportement par défaut pour gérer le cas si la méthode d' `PassToDebuggee` n'est pas appelée.  
  
## Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md)