---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b603f7e5b9b42b387df7922068d690762726b0d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494521"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugExceptionEvent2::GetException](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexceptionevent2-getexception).  
  
Obtient une description détaillée de l’exception qui a déclenché cet événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in, out] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure est remplie avec la description de l’exception.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 (C++ uniquement) L’appelant est chargé de libérer toutes les chaînes dans le [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure, ainsi que de libérer le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet dans la structure.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

