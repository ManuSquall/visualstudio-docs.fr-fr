---
title: IDebugExceptionEvent2::GetException | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ff936ca2da3025cd7ff8a7117f0227cd343b152e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Obtient une description détaillée de l’exception qui a déclenché cet événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```c#  
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
