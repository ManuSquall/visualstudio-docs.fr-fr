---
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4aa7bbad1361053d86c59fabb58027c955856222
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343117"
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
[in] Une combinaison d’indicateurs de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) énumération qui spécifie les champs dans la liste énumérée [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures doivent être renseignés.

`dwRadix`\
[in] Spécifie la base à utiliser dans toutes les informations numériques de mise en forme.

`guidFilter`\
[in] GUID du filtre utilisé avec le `dwAttribFilter` et `pszNameFilter` paramètres pour sélectionner les `DEBUG_PROPERTY_INFO` enfants doivent être énumérés. Par exemple, `guidFilterLocals` filtres pour les variables locales.

`dwAttribFilter`\
[in] Une combinaison d’indicateurs de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération qui spécifie le type d’objets à énumérer, par exemple `DBG_ATTRIB_METHOD` pour toutes les méthodes qui peuvent être des enfants de cette propriété. Utilisé en association avec le `guidFilter` et `pszNameFilter` paramètres.

`pszNameFilter`\
[in] Le nom du filtre utilisé avec le `guidFilter` et `dwAttribFilter` paramètres pour sélectionner les `DEBUG_PROPERTY_INFO` enfants doivent être énumérés. Par exemple, ce paramètre aux filtres de « MyX » pour tous les enfants avec le nom « MyX ».

`dwTimeout`\
[in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`ppEnum`\
[out] Retourne un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet contenant une liste des propriétés enfants.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)