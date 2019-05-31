---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6d3edeb677af728b1a0fd0e9cf8685e7919d79e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317931"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Crée un énumérateur pour les champs du conteneur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Paramètres
`dwKindFilter`\
[in] Une combinaison de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que vous sélectionnez les champs à énumérer. Types de champ peuvent décrire des types de stockage, telles que la classe ou aux informations de primitives ou spécifiques, comme local, paramètre ou pointeur « this ».

`dwModifiersFilter`\
[in] Une combinaison de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que vous sélectionnez les champs à énumérer. Modificateurs de champ peuvent être des autorisations d’accès, tels que public ou privé ou des informations de stockage, comme virtuelle, statique ou finale.

`pszNameFilter`\
[in] Le nom du champ à énumérer. Cela peut être une valeur null si tous les champs doivent être retournées.

`nameMatch`\
[in] Une valeur comprise entre le [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) énumération qui détermine si la recherche respecte la casse ou non.

`ppEnum`\
[out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des champs. Retourne une valeur null si aucun champ.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ou S_FALSE si aucun champ. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le `dwKindFilter`, `dwModifiersFilter`, et `pszNameFilter` paramètres peuvent être combinés, par exemple, pour sélectionner toutes les méthodes virtuelles publics nommés « MyMethod ».

## <a name="see-also"></a>Voir aussi
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)