---
title: IDebugMemoryContext2::GetName ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8a13c078340eafcff9440e41afd468ba95f9849
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727452"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Récupère le nom affichage utilisateur pour ce contexte.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Paramètres
`pbstrName`\
[out] Retourne le nom du contexte de la mémoire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le nom d’un contexte de mémoire n’est normalement pas utilisé.

## <a name="see-also"></a>Voir aussi
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
