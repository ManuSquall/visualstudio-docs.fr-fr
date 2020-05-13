---
title: IDebugEnumField::GetValueDeString (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730259"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Cette méthode renvoie la valeur associée au nom d’une constante de recensement.

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
[dans] Une chaîne spécifiant le nom pour lequel obtenir la valeur. Notez que pour le C, il s’agit d’une large chaîne de caractères.

`pValue`\
[out] Retourne la valeur numérique associée.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, `S_FALSE`les retours , si le nom ne fait pas partie de l’énumération, ou un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est sensible aux cas. Si une recherche insensible au cas est nécessaire (par exemple, dans une langue telle que Visual Basic où les noms ne sont pas sensibles aux cas), utilisez [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Voir aussi
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
