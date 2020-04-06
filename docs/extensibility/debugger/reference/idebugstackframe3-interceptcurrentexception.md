---
title: IDebugStackFrame3::InterceptCurrentException (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719483"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Appelé par le débbuggeur sur le cadre de pile actuelle quand il veut intercepter l’exception actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Paramètres
`dwFlags`\
[dans] Spécifie différentes actions. Actuellement, seule la [valeur](../../../extensibility/debugger/reference/intercept-exception-action.md) `IEA_INTERCEPT` INTERCEPT_EXCEPTION_ACTION est prise en charge et doit être spécifiée.

`pqwCookie`\
[out] Valeur unique identifiant une exception particulière.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

 Ce qui suit sont les retours d’erreur les plus courants.

|Error|Description|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|L’exception actuelle ne peut pas être interceptée.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Le cadre d’exécution actuel n’a pas encore été recherché pour un gestionnaire.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Cette méthode n’est pas prise en charge pour ce cadre.|

## <a name="remarks"></a>Notes
 Lorsqu’une exception est lancée, le débbuggeur prend le contrôle du temps d’exécution à des points clés au cours du processus de manutention d’exception. Pendant ces moments clés, le débbuggeur peut demander le cadre de pile en cours si le cadre veut intercepter l’exception. De cette façon, une exception interceptée est essentiellement un gestionnaire d’exception sur la volée pour un cadre de pile, même si ce cadre de pile n’a pas un gestionnaire d’exception (par exemple, un bloc d’essai/capture dans le code de programme).

 Lorsque le débbuggeur veut savoir si l’exception doit être interceptée, il appelle cette méthode sur l’objet de cadre de pile actuel. Cette méthode est responsable de la gestion de tous les détails de l’exception. Si [l’interface IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) n’est pas implémentée ou si la `InterceptStackException` méthode renvoie une erreur, le débbuggeur continue de traiter l’exception normalement.

> [!NOTE]
> Les exceptions ne peuvent être interceptées que dans le code géré, c’est-à-dire lorsque le programme qui est débogé est exécuté en vertu du temps d’exécution .NET. Bien sûr, les exécutants de `InterceptStackException` langage tiers peuvent implémenter dans leurs propres moteurs de débogé s’ils le souhaitent.

 Une fois l’interception terminée, un [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) est signalé.

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
