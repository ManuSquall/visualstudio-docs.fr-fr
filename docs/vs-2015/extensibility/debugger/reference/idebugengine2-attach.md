---
title: IDebugEngine2::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa03f59945b1e51d0c86aee48dde27d0fa4b326b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177084"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Attache un moteur de débogage (dé) à un programme ou des programmes. Appelé par le Gestionnaire de session de débogage (SDM) lors de l’Allemagne est en cours d’exécution in-process pour le SDM.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProgram`  
 [in] Un tableau de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objets qui représentent des programmes à joindre à. Il s’agit de programmes de port.  
  
 `rgpProgramNodes`  
 [in] Un tableau de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objets qui représentent des nœuds de programme, un pour chaque programme. Les nœuds de programme dans ce tableau représentent les mêmes programmes comme dans `pProgram`. Les nœuds de programme se voient attribuer afin que l’Allemagne peut identifier les programmes à attacher à.  
  
 `celtPrograms`  
 [in] Nombre de programmes et/ou des nœuds de programme dans le `pProgram` et `rgpProgramNodes` tableaux.  
  
 `pCallback`  
 [in] Le [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet à utiliser pour envoyer des événements de débogage vers le SDM.  
  
 `dwReason`  
 [in] Une valeur comprise entre le [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) énumération qui spécifie la raison de l’attachement de ces programmes. Pour plus d'informations, consultez la section Remarques.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Il existe trois raisons pour l’attachement à un programme, comme suit :  
  
-   `ATTACH_REASON_LAUNCH` Indique que l’Allemagne est attacher au programme, car l’utilisateur a lancé le processus qui le contient.  
  
-   `ATTACH_REASON_USER` Indique que l’utilisateur a demandé explicitement le DE joindre à un programme (ou le processus qui contient un programme).  
  
-   `ATTACH_REASON_AUTO` Indique le DE concerne l’attachement à un programme particulier, car il est déjà débogage autres programmes dans un processus particulier. On parle également l’attachement automatique.  
  
 Lorsque cette méthode est appelée, l’Allemagne a besoin envoyer ces événements de séquence :  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (si elle n'a pas déjà été envoyée pour une instance particulière du moteur de débogage)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 En outre, si la raison de l’attachement est `ATTACH_REASON_LAUNCH`, l’Allemagne doit envoyer le [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) événement.  
  
 Une fois l’obtient DE la [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) de l’objet correspondant au programme en cours de débogage, il peut être interrogé pour n’importe quelle interface privée.  
  
 Avant d’appeler les méthodes d’un nœud de programme dans le tableau donné par `pProgram` ou `rgpProgramNodes`, l’emprunt d’identité, le cas échéant, doit être activée sur le `IDebugProgram2` interface qui représente le nœud de programme. Normalement, toutefois, cette étape n’est pas nécessaire. Pour plus d’informations, consultez [des problèmes de sécurité](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

