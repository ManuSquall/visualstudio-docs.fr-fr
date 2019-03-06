---
title: IDebugProgramDestroyEventFlags2::GetFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugProgramDestroyEventFlags2::GetFlags
ms.assetid: dd53bd0c-459a-4077-ba81-780defb71e87
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b163da7d37983b41cb27d8db799817376784346
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691993"
---
# <a name="idebugprogramdestroyeventflags2getflags"></a>IDebugProgramDestroyEventFlags2::GetFlags
Récupère le programme détruire des indicateurs.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetFlags(
   PROGRAM_DESTROY_FLAGS* pdwFlags
);
```

```csharp
public int GetFlags(
   out enum_PROGRAM_DESTROY_FLAGS pdwFlags
);
```

#### <a name="parameters"></a>Paramètres
 `pdwFlags`

 [out] Représente le programme détruire des indicateurs.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)
- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)