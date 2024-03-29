---
description: Définit la valeur d’une propriété à partir d’une chaîne donnée.
title: 'IDebugProperty2 :: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e3a80c6d5c6e9f3b7f5d9b68ed08dd0b39d940e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064734"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Définit la valeur d’une propriété à partir d’une chaîne donnée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Paramètres
`pszValue`\
dans Chaîne contenant la valeur à définir.

`nRadix`\
dans Base à utiliser pour interpréter toutes les informations numériques. La valeur peut être 0 pour tenter de déterminer la base automatiquement.

`dwTimeout`\
dans Spécifie la durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur. Le tableau suivant présente d’autres valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La chaîne n’a pas pu être convertie en valeur de propriété ou la valeur de la propriété n’a pas pu être définie.|
|`E_SETVALUE_VALUE_IS_READONLY`|la propriété est en lecture seule.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
