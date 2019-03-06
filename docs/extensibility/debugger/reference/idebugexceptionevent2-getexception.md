---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79385348aa9290f26a34b99dbd2d6f68cb92dc8a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680280"
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

 [in, out] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure est remplie avec la description de l’exception.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes

 (C++ uniquement) L’appelant est chargé de libérer toutes les chaînes dans le [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure, ainsi que de libérer le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet dans la structure.

## <a name="see-also"></a>Voir aussi
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)