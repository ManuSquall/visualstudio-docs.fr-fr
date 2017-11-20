---
title: IDebugExceptionEvent2::GetException | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::GetException
helpviewer_keywords: IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cc68f7fb843e97e9333aa8d0223ed601df98273
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Obtient une description détaillée de l’exception qui a déclenché cet événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pExceptionInfo`  
 [dans, out] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure est remplie avec la description de l’exception.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 (C++ uniquement) L’appelant est responsable de la libération de toutes les chaînes dans le [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , ainsi que la libération de la structure du [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet dans la structure.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)