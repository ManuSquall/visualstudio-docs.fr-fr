---
title: IDebugProgramPublisher2::SetDebuggerPresent Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b551c644346b66d907fa4f75b11b24c8b9538e27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721606"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Indique à l’éditeur du programme qu’un débbuggeur est présent et en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>Paramètres
`fDebuggerPresent`\
[dans] Non-zéro`TRUE`( ) si un débbuggeur`FALSE`est présent, zéro ( ) si ce n’est pas le cas.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La présence ou l’absence d’un débbuggeur se reflète dans les données retournées de la méthode [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) : la valeur retournée là-bas est définie ou effacée par un appel préalable à la `SetDebuggerPresent` méthode.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
