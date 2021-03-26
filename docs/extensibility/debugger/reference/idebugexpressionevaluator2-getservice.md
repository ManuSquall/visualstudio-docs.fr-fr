---
description: Récupère un objet de service en fonction de son identificateur unique.
title: 'IDebugExpressionEvaluator2 :: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092005"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Récupère un objet de service en fonction de son identificateur unique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Paramètres
`uid`\
dans Identificateur unique du service à récupérer.

`ppService`\
à Retourne un objet qui représente le service.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cela peut être consommé par un évaluateur d’expression tiers pour obtenir des services à partir d’un autre évaluateur d’expression. Par exemple, cette méthode peut être utilisée pour obtenir l’interface du service du visualiseur à partir de l’évaluateur d’expression par défaut. Il est peu probable que les évaluateurs d’expressions tierces aient besoin d’implémenter cette interface.

## <a name="see-also"></a>Voir aussi
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
