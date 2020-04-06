---
title: IDebugProperty2::EnumChildren ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721508"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Récupère une liste des enfants de la propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`dwFields`\
[dans] Une combinaison de drapeaux de [l’énumération DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) qui précise quels champs dans les structures [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) énumérées doivent être remplis.

`dwRadix`\
[dans] Spécifie le radix à utiliser pour formater toute information numérique.

`guidFilter`\
[dans] GUID du filtre utilisé `dwAttribFilter` `pszNameFilter` avec le et `DEBUG_PROPERTY_INFO` les paramètres pour sélectionner les enfants qui doivent être énumérés. Par exemple, `guidFilterLocals` filtres pour les variables locales.

`dwAttribFilter`\
[dans] Une combinaison de drapeaux de [l’DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération qui précise quel type d’objets `DBG_ATTRIB_METHOD` à énumérer, par exemple pour toutes les méthodes qui pourraient être des enfants de cette propriété. Utilisé en combinaison `guidFilter` `pszNameFilter` avec le et les paramètres.

`pszNameFilter`\
[dans] Le nom du filtre `guidFilter` utilisé `dwAttribFilter` avec le `DEBUG_PROPERTY_INFO` et les paramètres pour sélectionner les enfants à énumérer. Par exemple, définir ce paramètre aux filtres « MyX » pour tous les enfants sous le nom de « MyX ».

`dwTimeout`\
[dans] Spécifie le temps maximum, en millisecondes, d’attendre avant de revenir de cette méthode. Utilisez-le `INFINITE` pour attendre indéfiniment.

`ppEnum`\
[out] Retourne un objet [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenant une liste des propriétés de l’enfant.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
