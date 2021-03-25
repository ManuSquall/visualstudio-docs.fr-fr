---
description: Affecte à la valeur de cette propriété la valeur de la référence donnée.
title: 'IDebugProperty2 :: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b370b4caa43ce6522b415233714eb15899b3051
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064772"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Affecte à la valeur de cette propriété la valeur de la référence donnée.

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
dans Tableau d’arguments à passer à la méthode setter de propriété de code managé. Si l’accesseur Set de la propriété ne prend pas d’arguments ou si cet objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ne fait pas référence à un tel accesseur Set de propriété, `rgpArgs` doit être une valeur null. Ce paramètre est généralement une valeur null.

`dwArgCount`\
dans Nombre d’arguments dans le `rgpArgs` tableau.

`pValue`\
dans Référence, sous la forme d’un objet [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , à la valeur à utiliser pour définir cette propriété.

`dwTimeout`\
dans Durée à prendre pour définir la valeur, en millisecondes. Une valeur typique est `INFINITE` . Cela a une incidence sur la durée que peut prendre une évaluation.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur, généralement l’un des éléments suivants :

|Error|Description|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|La définition de la valeur d’une référence n’est pas prise en charge.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La valeur ne peut pas être définie, car cette propriété fait référence à une méthode.|
|`E_SETVALUE_VALUE_IS_READONLY`|La valeur est en lecture seule et ne peut pas être définie.|
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
