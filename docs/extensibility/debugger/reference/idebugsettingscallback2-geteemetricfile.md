---
description: Récupère le fichier métrique de l’évaluateur d’expression en fonction du nom ou de la métrique.
title: 'IDebugSettingsCallback2 :: GetEEMetricFile | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9fdb578001ebb1999abb20f0f01861b7821175b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081371"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
Récupère le fichier métrique de l’évaluateur d’expression en fonction du nom ou de la métrique.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEEMetricFile(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricFile(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Paramètres
`guidLang`\
dans Identificateur unique du langage de programmation.

`guidVendor`\
dans Identificateur unique du fournisseur.

`pszMetric`\
dans Nom de la métrique.

`pbstrValue`\
à Retourne le contenu du fichier métrique sous forme de chaîne.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
