---
description: Cette méthode utilise une recherche ne respectant pas la casse pour retourner la valeur associée au nom d’une constante d’énumération.
title: 'IDebugEnumField :: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f853598c5d3c9b293c806e1db475c5053a1a208e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153220"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Cette méthode utilise une recherche ne respectant pas la casse pour retourner la valeur associée au nom d’une constante d’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Paramètres
`pszValue`\
dans Chaîne spécifiant le nom pour lequel obtenir la valeur. Notez que pour C++, il s’agit d’une chaîne de caractères larges.

`pValue`\
à Retourne la valeur numérique associée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` , si le nom ne fait pas partie de l’énumération ou un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode ne respecte pas la casse. Si une recherche respectant la casse est nécessaire (par exemple, dans un langage tel que C++ où les noms respectent la casse), utilisez [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Voir aussi
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
