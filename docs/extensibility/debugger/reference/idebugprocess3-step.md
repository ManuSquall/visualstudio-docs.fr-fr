---
title: IDebugProcess3::Étape Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723555"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Provoque le processus à l’étape d’une instruction ou d’une déclaration.

> [!NOTE]
> Cette méthode doit être utilisée au lieu de [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Paramètres
`pThread`\
[dans] Un objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) représentant le fil en cours de pas.

`sk`\
[dans] L’une des valeurs [de STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[dans] L’une des valeurs [de STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; retourne autrement le code d’erreur.

## <a name="remarks"></a>Notes
 Dans le cas où il ya une synchronisation de thread ou de communication entre les threads, d’autres threads dans le processus doit s’exécuter quand un thread particulier est en marche.

 **Avertissement** N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à [l’événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) pendant le traitement de cet appel; sinon le débbuggeur peut accrocher.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
