---
title: IDebugThread2::Suspend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd1987be34cf0f07ce5f37f074cd298a8135a4fa
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226396"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Interrompt un thread.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Paramètres
 `pdwSuspendCount`\

 [out] Retourne le nombre de suspend après l’opération de suspension.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Chaque appel à cette méthode incrémente le compteur de suspension supérieure à 0. Ce compteur de suspension s’affiche dans le **Threads** fenêtre de débogage.

 Pour chaque appel à cette méthode, il doit y avoir un appel ultérieur à la [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)