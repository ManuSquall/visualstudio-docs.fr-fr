---
title: "IDebugProcess3::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continue de s'exécuter ce processus consistant à l'état arrêté.  Tout état précédent de exécution \(par exemple une étape\) est désactivée et le démarrage du processus exécutant à nouveau.  
  
> [!NOTE]
>  Cette méthode doit être utilisée à la place d' [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## Syntaxe  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### Paramètres  
 `pThread`  
 \[in\]  un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) représentant le thread pour exécuter.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, le code d'erreur de retour.  
  
## Notes  
 Lorsque l'utilisateur commence l'exécution à partir de l'état arrêté dans les threads d'un autre processus, cette méthode est appelée sur ce processus.  Cette méthode est également appelée lorsque l'utilisateur sélectionne la commande de **Démarrer** dans le menu de **Débogage** dans l'IDE.  L'implémentation de cette méthode peut être aussi simple que l'appel de la méthode d' [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md) sur le thread actuel dans le processus.  
  
> [!WARNING]
>  N'envoyez pas d'événement arrêtant ou un événement \(synchrone\) immédiat est [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) tout en gérant cet appel ; sinon le débogueur peut se bloquer.  
  
## Voir aussi  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)