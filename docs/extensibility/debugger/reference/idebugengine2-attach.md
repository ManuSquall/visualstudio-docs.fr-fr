---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

joint un moteur de débogage \(DE\) à un programme ou programme.  Appelé par le gestionnaire de débogage de session \(SDM\) lorsque le De exécute in\-process au SDM.  
  
## Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### Paramètres  
 `pProgram`  
 \[in\]  Un tableau d'objets d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représentent des programmes à joindre.  ce sont des programmes de port.  
  
 `rgpProgramNodes`  
 \[in\]  Un tableau d'objets d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représentent des nœuds de programme, un pour chaque programme.  Les nœuds de programme dans ce tableau représentent les mêmes programmes que dans `pProgram`.  Les nœuds de programme sont fournis afin que le De puisse identifier les programmes pour attacher.  
  
 `celtPrograms`  
 \[in\]  Numéro de programmes et\/ou de nœuds de programme dans les tableaux d' `pProgram` et d' `rgpProgramNodes` .  
  
 `pCallback`  
 \[in\]  l'objet d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débogage au SDM.  
  
 `dwReason`  
 \[in\]  une valeur de l'énumération d' [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui spécifie la raison pour joindre ces programmes.  Pour plus d'informations, consultez la section Notes.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Il existe trois raisons pour attacher le débogueur à un programme, comme suit :  
  
-   `ATTACH_REASON_LAUNCH` indique que le De s'attache au programme étant donné que l'utilisateur a lancé le processus qui le contient.  
  
-   `ATTACH_REASON_USER` indique que l'utilisateur a demandé explicitement le De à attacher à un programme \(ou au processus qui contient un programme\).  
  
-   `ATTACH_REASON_AUTO` indique le De est attaché à un programme particulier car il débogue déjà d'autres programmes dans un processus particulier.  Il est également appelé auto\-attachement.  
  
 Lorsque cette méthode est appelée, le De doit envoyer ces événements dans l'ordre :  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) \(s'il n'a pas déjà été envoyé pour une instance particulière du moteur de débogage\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 En outre, si la raison de la jointure est `ATTACH_REASON_LAUNCH`, le De doit envoyer l'événement d' [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .  
  
 Une fois le De obtient l'objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) correspondant au programme en cours de débogage, il peut être interrogé pour toute interface privée.  
  
 Avant d'appeler les méthodes de nœud de programme dans le tableau donné par `pProgram` ou `rgpProgramNodes`, l'emprunt d'identité doit être activé, si nécessaire, sur l'interface d' `IDebugProgram2` qui représente le nœud de programme.  Normalement, toutefois, cette étape n'est pas nécessaire.  Pour plus d'informations, consultez [Problèmes de sécurité](../../../extensibility/debugger/security-issues.md).  
  
## Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)