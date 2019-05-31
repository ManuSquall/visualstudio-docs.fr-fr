---
title: IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 561f6727ca0273d5d59434a7bfdd0cdc00533754
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322193"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
Récupère un objet local évaluateur d’expression étant donné le nom de la mesure.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEELocalObject(
   REFGUID     guidLang,
   REFGUID     guidVendor,
   LPCWSTR     pszMetric,
   IUnknown ** ppUnk
);
```

```csharp
private int GetEELocalObject(
   ref Guid          guidLang,
   ref Guid          guidVendor,
   string            pszMetric,
   out System.Object ppUnk
);
```

## <a name="parameters"></a>Paramètres
`guidLang`\
[in] Identificateur unique du langage de programmation.

`guidVendor`\
[in] Identificateur unique du fournisseur.

`pszMetric`\
[in] Nom de la mesure.

`ppUnk`\
[out] Retourne l’expression objet local évaluateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)