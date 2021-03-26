---
description: Récupère une liste de tous les threads qui s’exécutent dans le processus.
title: 'IDebugProcess2 :: Enumthreads, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c502504b3a31f3e4689db34f907f9596b214877
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071608"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Récupère une liste de tous les threads qui s’exécutent dans le processus.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
à Retourne un objet [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) qui contient une liste de tous les threads dans tous les programmes du processus.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode énumère les threads en cours d’exécution dans chaque programme, puis les combine dans une vue de processus des threads. Un seul thread peut s’exécuter dans plusieurs programmes. Cette méthode énumère ce thread une seule fois.

 Cette méthode présente une liste des threads du processus sans doublons. Dans le cas contraire, pour énumérer les threads en cours d’exécution dans un programme particulier, utilisez la méthode [enumthreads,](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
