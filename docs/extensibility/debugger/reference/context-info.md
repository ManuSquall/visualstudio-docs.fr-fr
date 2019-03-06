---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c41a155fb3a85bcb9f0b0e5eae461f2ae172c7e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709978"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Un contexte de la mémoire ou d’un contexte de code décrite par cette structure.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Membres
Une combinaison d’indicateurs de l’il de dwFields [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) énumération qui spécifie quels champs sont renseignés<strong>.</strong>

bstrModuleUrl le nom du module où se trouve le contexte.

bstrFunction le nom de la fonction où se trouve le contexte.

posFunctionOffset A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure qui identifie l’offset de ligne et colonne de la fonction associée au contexte de code.

bstrAddress l’adresse dans le code où se trouve le contexte donné.

bstrAddressOffset le décalage de l’adresse dans le code où se trouve le contexte donné.

bstrAddressAbsolute l’adresse absolue en mémoire où se trouve le contexte donné.

## <a name="remarks"></a>Notes
Cette structure est retournée à partir d’un appel à la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) (méthode).

En règle générale pour cette structure est à l’appui d’un **mémoire** fenêtre de débogage.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
