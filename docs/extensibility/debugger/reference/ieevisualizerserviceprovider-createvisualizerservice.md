---
description: Cette méthode crée un service de visualiseur.
title: 'IEEVisualizerServiceProvider :: CreateVisualizerService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f8695b578b1a069fd8fe8fa2afdd3a7c21ccd92
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086753"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Cette méthode crée un service de visualiseur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Paramètres
`binder`\
dans Objet [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) passé à [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
dans Objet [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) passé à `IDebugParsedExpression::EvaluateSync` .

`pAddress`\
dans Objet [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) passé à `IDebugParsedExression::EvaluateSync` .

`dataProvider`\
dans Objet implémentant l’interface [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (fournie par l’évaluateur d’expression).

`ppService`\
à Service créé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les `binder` `pSymProv` paramètres, et `pAddress` ont tous été passés à la `IDebugParsedExpression::EvaluateSync` méthode. `CreateVisualizerService` doit être appelé uniquement à partir de dans le cadre `IDebugParsedExpression::EvaluateSync` de la prise en charge d’un évaluateur d’expression pour les visualiseurs de type.

## <a name="see-also"></a>Voir aussi
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
