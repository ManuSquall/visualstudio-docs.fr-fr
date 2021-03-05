---
description: Appelé lorsque le traitement d’une exception interceptée est terminé.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70fb92c20eab3700043a11f8544896bbbce3b7c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172530"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Appelé lorsque le traitement d’une exception interceptée est terminé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Paramètres
`pqwCookie`\
à Valeur unique associée à l’exception qui a été interceptée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 Une fois que la méthode [InterceptCurrentException,](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) a terminé la gestion d’une exception interceptée, elle envoie l’événement [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) . Le gestionnaire peut utiliser la `GetInterceptCookie` méthode pour récupérer la valeur unique associée à l’exception (la même valeur passée à la `InterceptCurrentException` méthode).

## <a name="see-also"></a>Voir aussi
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
