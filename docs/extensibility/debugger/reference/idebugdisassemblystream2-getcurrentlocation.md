---
title: IDebugDisassemblyStream2::GetCurrentLocation (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 440afc26688522da5cc8b6c20b2712872b4ce6b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732225"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
Renvoie un identifiant de localisation de code qui représente l’emplacement actuel du code.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCurrentLocation( 
   UINT64* puCodeLocationId
);
```

```csharp
int GetCurrentLocation( 
   out ulong puCodeLocationId
);
```

## <a name="parameters"></a>Paramètres
`puCodeLocationId`\
[out] Retourne l’identifiant de localisation du code. Consultez la section Remarques pour la méthode [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) pour une description d’un identifiant de localisation de code.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’identifiant de localisation du code peut être converti en contexte de code en appelant la méthode [GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>Voir aussi
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
