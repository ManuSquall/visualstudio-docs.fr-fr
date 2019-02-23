---
title: IDebugSettingsCallback2::GetEEMetricDword | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 475a2a22e148c1b2849d469889492f7eb271e7e1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697648"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
Récupère une valeur qui correspond à la mesure spécifiée de l’évaluateur d’expression.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEEMetricDword(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   DWORD*  pdwValue
);
```

```csharp
private int GetEEMetricDword(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out uint pdwValue
);
```

#### <a name="parameters"></a>Paramètres
 `guidLang`

 [in] Identificateur unique du langage de programmation.

 `guidVendor`

 [in] Identificateur unique du fournisseur.

 `pszMetric`

 [in] Nom de la mesure.

 `pdwValue`

 [out] Retourne la valeur qui correspond à la chaîne de métrique.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)