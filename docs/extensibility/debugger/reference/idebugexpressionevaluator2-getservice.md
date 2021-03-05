---
description: Récupère un objet de service en fonction de son identificateur unique.
title: 'IDebugExpressionEvaluator2 :: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a522cefec514baf8b7d8219846587f18c37559a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152362"
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
