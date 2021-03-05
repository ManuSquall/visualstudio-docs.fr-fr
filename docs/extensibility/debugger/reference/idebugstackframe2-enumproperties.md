---
description: Crée un énumérateur pour les propriétés associées au frame de pile, telles que les variables locales.
title: 'IDebugStackFrame2 :: EnumProperties, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40298e505f0d3ccbba200c5487a1bf1d6723f5b2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145961"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Crée un énumérateur pour les propriétés associées au frame de pile, telles que les variables locales.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`dwFieldSpec`\
dans Combinaison d’indicateurs de l’énumération [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) qui spécifie les champs dans les structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) énumérées à remplir.

`nRadix`\
dans Base à utiliser pour mettre en forme les informations numériques.

`refiid`\
dans GUID d’un filtre utilisé pour sélectionner les structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) à énumérer, telles que `guidFilterLocals` .

`dwTimeout`\
dans Durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`pcelt`\
à Retourne le nombre de propriétés énumérées. Cela revient à appeler la méthode [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) .

`ppEnum`\
à Retourne un objet [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenant une liste des propriétés souhaitées.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Étant donné que cette méthode permet de récupérer toutes les propriétés sélectionnées avec un seul appel, il est plus rapide d’appeler les méthodes [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) et [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
