---
title: "IDebugProgram2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

attachés au programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### Paramètres  
 `pCallback`  
 \[in\]  un objet d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour la notification d'événements de débogage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre des codes d'erreur possibles.  
  
|Valeur|Description|  
|------------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le programme spécifié est déjà attachée au débogueur.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s'est produite pendant la procédure d'attachement.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programme de bureau ne peut pas être attaché au débogueur.|  
  
## Notes  
 Un moteur \(DE\) de débogage n'appelle jamais cette méthode pour attacher un programme.  Si le De fonctions dans l'espace d'adressage du programme, la méthode d' [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) est appelée.  Si s'exécute dans une session de débogage l'espace d' \(SDM\)adressage du gestionnaire, la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) est appelée.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)