---
title: IDebugProgram2::Execute Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722980"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continue à exécuter ce programme à partir d’un état arrêté. Tout état d’exécution précédent (comme une étape) est effacé, et le programme commence à exécuter à nouveau.

> [!NOTE]
> Cette méthode est déconseillée. Utilisez la méthode [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lorsque l’utilisateur commence l’exécution à partir d’un état arrêté dans le thread d’un autre programme, cette méthode est appelée sur ce programme. Cette méthode est également appelée lorsque l’utilisateur sélectionne la commande **Démarrer** à partir du menu **Debug** dans l’IDE. La mise en œuvre de cette méthode peut être aussi simple que d’appeler la méthode [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) sur le fil actuel dans le programme.

> [!WARNING]
> N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à [l’événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) pendant le traitement de cet appel; sinon le débbuggeur peut accrocher.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)
