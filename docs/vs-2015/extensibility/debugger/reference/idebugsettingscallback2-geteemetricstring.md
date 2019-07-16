---
title: IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f498bb22c5830434d11a560fa139e77850244b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155175"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Récupère la chaîne de valeur d’une métrique d’évaluateur d’expression étant donné son nom.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

#### <a name="parameters"></a>Paramètres
 `guidLang`

 [in] Identificateur unique du langage de programmation.

 `guidVendor`

 [in] Identificateur unique du fournisseur.

 `pszMetric`

 [in] Nom de la mesure.

 `pbstrValue`

 [out] Retourne la chaîne de valeur métrique.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)