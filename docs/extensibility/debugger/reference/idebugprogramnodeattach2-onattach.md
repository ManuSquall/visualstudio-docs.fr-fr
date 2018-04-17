---
title: IDebugProgramNodeAttach2::OnAttach | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c7c7e6f7ef640b192b7ed8c57ac87375a5ad189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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