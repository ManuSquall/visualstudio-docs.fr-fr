---
title: IDebugExceptionEvent2:CanPassToDebuggee (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729873"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Détermine si le moteur de débogé (DE) prend en charge la possibilité de passer cette exception au programme qui est débogé lorsque l’exécution reprend.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valeur de retour
 Les `S_OK` retours (l’exception peut être `S_FALSE` transmis au programme) ou (l’exception ne peut pas être transmise).

## <a name="remarks"></a>Notes
 Le DE doit avoir une action par défaut pour passer au débbuggee. L’IDE peut recevoir [l’événement IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) et `CanPassToDebuggee` appeler la méthode [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sans appeler la méthode. Par conséquent, le DE devrait avoir un cas par défaut pour transmettre l’exception ou non.

## <a name="see-also"></a>Voir aussi
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
