---
title: IDebugProperty2::GetPropertyInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c250cdfdef37a1c6eddfb266909deca1cc515f1c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709159"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Obtient le [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure qui décrit une propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

#### <a name="parameters"></a>Paramètres
 `dwFields`

 [in] Une combinaison de valeurs à partir de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) énumération qui spécifie quels champs doivent être remplis dans la `pPropertyInfo` structure.

 `nRadix`

 [in] Base à utiliser dans toutes les informations numériques de mise en forme.

 `dwTimeout`

 [in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

 `rgpArgs`

 [in, out] Réservé pour une utilisation ultérieure ; la valeur est une valeur null.

 `dwArgCount`

 [in] Réservé pour une utilisation ultérieure ; la valeur zéro.

 `pPropertyInfo`

 [out] Un [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure est remplie avec la description de la propriété.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)