---
title: 'IDebugEngine2 :: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62be3ce13ecbc3180cf2bbcce26b04f3d79edb1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731156"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Demande que tous les programmes débogués par ce moteur de débogage (DE) interrompent l’exécution lors de la prochaine tentative d’exécution de l’un de leurs threads.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est asynchrone : un événement [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) est envoyé lorsque le programme tente ensuite de s’exécuter après l’appel de cette méthode.

## <a name="see-also"></a>Voir aussi
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
