---
title: IDebugProperty2::SetValueAsReference (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721251"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Définit la valeur de cette propriété à la valeur de la référence donnée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Paramètres
`rgpArgs`\
[dans] Une panoplie d’arguments à transmettre à la propriété de code géré setter. Si le setter de propriété ne prend pas d’arguments ou si cet objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ne se réfère pas à un tel setter propriété, `rgpArgs` devrait être une valeur nulle. Ce paramètre est généralement une valeur nulle.

`dwArgCount`\
[dans] Le nombre d’arguments dans le `rgpArgs` tableau.

`pValue`\
[dans] Une référence, sous la forme d’un objet [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) à la valeur à utiliser pour définir cette propriété.

`dwTimeout`\
[dans] Combien de temps à prendre pour définir la valeur, en millisecondes. Une valeur `INFINITE`typique est . Cela affecte le temps que toute évaluation possible peut prendre.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur, généralement l’un des éléments suivants :

|Error|Description|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|La définition de la valeur d’une référence n’est pas prise en charge.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La valeur ne peut pas être définie, car cette propriété se réfère à une méthode.|
|`E_SETVALUE_VALUE_IS_READONLY`|La valeur est lue uniquement et ne peut pas être définie.|
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
