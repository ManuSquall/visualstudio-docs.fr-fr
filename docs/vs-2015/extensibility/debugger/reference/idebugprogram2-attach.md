---
title: IDebugProgram2::Attach | Microsoft Docs
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
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 59125c4b8237f1c22b556ed060e5254c8fbcac4d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284997"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Attache au programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet à utiliser pour la notification d’événement de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant présente certains codes d’erreur possibles.  
  
|Value|Description|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le programme spécifié est déjà attaché au débogueur.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s’est produite lors de la procédure d’attachement.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programme de bureau ne peut pas être attaché au débogueur.|  
  
## <a name="remarks"></a>Notes  
 Un moteur de débogage (dé) n’appelle jamais cette méthode pour attacher à un programme. Si le dé s’exécute dans l’espace d’adressage du programme, le [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) méthode est appelée. Si l’espace d’adressage DE s’exécute dans le Gestionnaire de débogage de session (SDM) le [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)

