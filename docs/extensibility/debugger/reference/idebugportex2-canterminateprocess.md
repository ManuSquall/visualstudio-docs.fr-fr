---
title: IDebugPortEx2::CanTerminateProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf3f68ef2b6e8ed444f090bee9ac6918652b8b1c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209087"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Détermine si un processus peut être arrêté.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanTerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
HRESULT CanTerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>Paramètres
`pPortProcess`\
[in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet représentant la fin du processus.

## <a name="return-value"></a>Valeur de retour
 Retourne `S_OK` si le processus peut être arrêté ; sinon, retourne `S_FALSE`.

## <a name="see-also"></a>Voir aussi
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)