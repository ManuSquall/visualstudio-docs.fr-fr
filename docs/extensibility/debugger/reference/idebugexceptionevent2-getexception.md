---
description: Obtient une description détaillée de l’exception qui a déclenché cet événement.
title: 'IDebugExceptionEvent2 :: GetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72457b1b8931d028f555e7f9354f34b133fa79bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084777"
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

## <a name="parameters"></a>Paramètres
`pExceptionInfo`\
[in, out] Structure [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) qui est remplie avec la description de l’exception.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes

 [C++ uniquement] L’appelant est chargé de libérer des chaînes dans la structure [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , ainsi que de libérer l’objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dans la structure.

## <a name="see-also"></a>Voir aussi
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
