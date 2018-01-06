---
title: IDebugProgram2::GetProgramId | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetProgramId
helpviewer_keywords: IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5edf51bfa37cfdca7779417cd01320a1ee89cbd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Obtient un GUID pour ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pguidProgramId`  
 [out] Retourne le `GUID` pour ce programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Un moteur de débogage (DE) doit retourner l’identificateur de programme à l’origine passée à la [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthodes. Cela permet l’identification du programme dans le débogueur composants.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)