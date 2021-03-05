---
description: Cette méthode retourne la valeur associée au nom d’une constante d’énumération.
title: 'IDebugEnumField :: GetValueFromString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a4ab2950667ba9268335f2e0dbca1c0ce5183bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153298"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Cette méthode retourne la valeur associée au nom d’une constante d’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
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
 Cette méthode est sensible à la casse. Si une recherche ne respectant pas la casse est nécessaire (par exemple, dans un langage tel que Visual Basic où les noms ne respectent pas la casse), utilisez [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Voir aussi
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
