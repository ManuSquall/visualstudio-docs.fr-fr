---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

DÉCONSEILLÉ.  NE SUR UTILISEZ NOT.  
  
## Syntaxe  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### Paramètres  
 `pMDMProgram`  
 \[in\]  L'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) à laquelle représente le programme à attacher.  
  
 `pCallback`  
 \[in\]  l'interface d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) à utiliser pour envoyer des événements de débogage au SDM.  
  
 `dwReason`  
 \[in\]  Une valeur de l'énumération d' [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui spécifie la raison pour attacher.  
  
## Valeur de retour  
 Une implémentation doit toujours retourner `E_NOTIMPL`.  
  
## Notes  
  
> [!WARNING]
>  À partir de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], cette méthode est plus utilisée et ne doivent toujours retourner `E_NOTIMPL`.  Consultez l'interface d' [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pour une autre approche si le nœud de programme doit pointer ne peut pas être attaché ou si le nœud de programme définit simplement le programme `GUID`. Sinon, implémentez la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## avant Visual Studio 2005  
 Cette méthode doit être implémentée uniquement si le De fonctions dans l'espace d'adressage du programme débogué.  Sinon, cette méthode doit retourner `S_FALSE`.  
  
 Lorsque cette méthode est appelée, le De doit envoyer l'objet événement d' [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , s'il n'a pas déjà été envoyé pour cette instance de l'interface d' [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , ainsi que des objets événement d' [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et d' [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) .  L'objet événement d' [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) est ensuite envoyé si le paramètre d' `dwReason` est `ATTACH_REASON_LAUNCH`.  
  
 Le De doit appeler la méthode d' [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sur l'objet d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) fourni par l'objet événement d' [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , et doit stocker que le GUID du programme dans les données d'instance pour l'objet d' `IDebugProgram2` implémenté par le De.  
  
## Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)