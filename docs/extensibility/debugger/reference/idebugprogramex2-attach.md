---
title: IDebugProgramEx2::Attach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEx2::Attach
helpviewer_keywords: IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 440a4ce6b008efe541187d1d99d886f4c7c5f9ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Joindre une session à un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet qui représente la fonction de rappel qui envoie des événements pour le moteur de débogage attaché.  
  
 `dwReason`  
 [in] Une valeur à partir de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) énumération qui décrit la raison de l’opération d’attachement.  
  
 `pSession`  
 [in] Une valeur qui identifie de façon unique la session qui s’attache au programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Cette méthode doit retourner `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si le programme est déjà attaché.  
  
## <a name="remarks"></a>Notes  
 Le port qui contient le programme peut utiliser la valeur de `pSession` pour déterminer quelle session tente de se joindre au programme. Par exemple, si un port permet la session de débogage qu’un seul s’attacher à un processus à la fois, le port peut déterminer si la même session est déjà attachée à d’autres programmes dans le processus.  
  
> [!NOTE]
>  L’interface est passée dans `pSession` doit être traité uniquement en tant que cookie, une valeur qui identifie de façon unique le Gestionnaire de session de débogage attachement à ce programme ; aucune des méthodes sur l’interface fournie sont fonctionnels.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)