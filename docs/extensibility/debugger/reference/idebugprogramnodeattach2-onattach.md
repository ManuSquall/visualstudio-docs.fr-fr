---
title: IDebugProgramNodeAttach2::OnAttach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords: IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6b0f74ef5b14fb9e8971c0d539cc2e875658341
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
S’attache au programme associé ou diffère du processus d’attachement à la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidProgramId`  
 [in] `GUID` à affecter au programme associé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si le [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode ne doit pas être appelée. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée pendant le processus d’attachement, avant que le [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée. Le `OnAttach` méthode peut exécuter le processus d’attachement (dans ce cas, cette méthode retourne `S_FALSE`) ou différer le processus d’attachement à la `IDebugEngine2::Attach` (méthode) (le `OnAttach` retourne de la méthode `S_OK`). Dans les deux cas, le `OnAttach` méthode peut définir le `GUID` du programme débogué sur la donnée `GUID`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)