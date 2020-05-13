---
title: IDebugExtendedField::GetExtendedKind (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 942b14af9907e2c026372f295a59ac1f22f78bc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729078"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
Récupère le type de champ étendu spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExtendedKind(
   FIELD_KIND_EX* pdwKind
);
```

```csharp
int GetExtendedKind(
   ref enum_FIELD_KIND_EX pdwKind
);
```

## <a name="parameters"></a>Paramètres
`pdwKind`\
[dans, dehors] Valeur de [l’énumération FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) qui définit le genre de champ.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
