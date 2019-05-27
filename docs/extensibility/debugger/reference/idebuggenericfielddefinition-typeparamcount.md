---
title: IDebugGenericFieldDefinition::TypeParamCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef015ed3313d2de8df77d1058adde24691e95962
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200579"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
Récupère le nombre de paramètres de type qui sont associés au champ générique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT TypeParamCount(
   ULONG32* pcParams
);
```

```csharp
int TypeParamCount(
   ref uint pcParams
);
```

## <a name="parameters"></a>Paramètres
`pcParams`\
[in, out] Nombre de paramètres de type.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si liste\<T >, cette méthode retourne 1 et, s’il liste\<T1, T2 >, cette méthode retourne la valeur 2. Cette méthode retourne 0 si aucun paramètre de type.

## <a name="see-also"></a>Voir aussi
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)