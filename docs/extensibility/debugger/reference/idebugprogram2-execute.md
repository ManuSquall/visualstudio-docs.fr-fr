---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Continue de s'exécuter ce programme d'un état arrêté.  Tout état précédent de exécution \(par exemple une étape\) est désactivé, et le démarrage du programme qui s'exécute à nouveau.  
  
> [!NOTE]
>  Cette méthode est déconseillée.  Employez plutôt la méthode [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md).  
  
## Syntaxe  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Lorsque l'utilisateur commence l'exécution à partir de l'état arrêté dans les threads d'un autre programme, cette méthode est appelée sur ce programme.  Cette méthode est également appelée lorsque l'utilisateur sélectionne la commande de **Démarrer** dans le menu de **Débogage** dans l'IDE.  L'implémentation de cette méthode peut être aussi simple que l'appel de la méthode d' [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md) sur le thread actuel dans le programme.  
  
> [!WARNING]
>  N'envoyez pas d'événement arrêtant ou un événement \(synchrone\) immédiat est [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) tout en gérant cet appel ; sinon le débogueur peut se bloquer.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)