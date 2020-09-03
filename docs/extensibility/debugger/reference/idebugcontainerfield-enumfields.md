---
title: 'IDebugContainerField :: EnumFields | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733222"
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
dans Combinaison de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes qui sélectionnent les champs à énumérer. Les types de champs peuvent décrire des types de stockage, tels que la classe ou la primitive, ou des informations spécifiques, comme un pointeur local, de paramètre ou « this ».

`dwModifiersFilter`\
dans Combinaison de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes qui sélectionnent les champs à énumérer. Les modificateurs de champ peuvent être des autorisations d’accès, telles que des informations publiques ou privées, ou des informations de stockage, telles que Virtual, static ou final.

`pszNameFilter`\
dans Nom du champ à énumérer. Il peut s’agir d’une valeur null si tous les champs doivent être retournés.

`nameMatch`\
dans Valeur de l’énumération [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) qui contrôle si la recherche respecte ou non la casse.

`ppEnum`\
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de champs. Retourne une valeur null s’il n’y a aucun champ.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ou S_FALSE s’il n’y a aucun champ. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les `dwKindFilter` `dwModifiersFilter` paramètres, et `pszNameFilter` peuvent être combinés, par exemple, pour sélectionner toutes les méthodes virtuelles publiques nommées « MyMethod ».

## <a name="see-also"></a>Voir aussi
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
