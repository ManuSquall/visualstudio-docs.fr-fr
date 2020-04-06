---
title: IDebugContainerField::EnumFields - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733222"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Crée un enumérateur pour les champs du conteneur.

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
[dans] Une combinaison de [constantes FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) qui sélectionnent les champs à énumérer. Les types de terrain peuvent décrire les types de stockage, tels que la classe ou primitive, ou des informations spécifiques, telles que locale, paramètre, ou «ce» pointeur.

`dwModifiersFilter`\
[dans] Une combinaison de [constantes FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) qui sélectionnent les champs à énumérer. Les modificateurs de champ peuvent être des autorisations d’accès, telles que des informations publiques ou privées, ou des informations de stockage, telles que virtuelles, statiques ou définitives.

`pszNameFilter`\
[dans] Le nom du champ à énumérer. Cela peut être une valeur nulle si tous les champs doivent être retournés.

`nameMatch`\
[dans] Une valeur du [recensement NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) qui contrôle si la recherche est sensible au cas ou non.

`ppEnum`\
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des champs. Retourne une valeur nulle s’il n’y a pas de champs.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou S_FALSE s’il n’y a pas de champs. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le `dwKindFilter` `dwModifiersFilter`, `pszNameFilter` , et les paramètres peuvent être combinés, par exemple, pour sélectionner toutes les méthodes virtuelles publiques nommées "MyMethod".

## <a name="see-also"></a>Voir aussi
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
