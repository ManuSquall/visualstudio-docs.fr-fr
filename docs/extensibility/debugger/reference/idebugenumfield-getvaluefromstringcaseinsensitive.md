---
title: IDebugEnumField::GetValueFromStringCaseInsensitive (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730250"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Cette méthode utilise une recherche insensible aux cas pour retourner la valeur associée au nom d’une constante de recensement.

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
[dans] Une chaîne spécifiant le nom pour lequel obtenir la valeur. Notez que pour le C, il s’agit d’une large chaîne de caractères.

`pValue`\
[out] Retourne la valeur numérique associée.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, `S_FALSE`les retours , si le nom ne fait pas partie de l’énumération, ou un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est insensible aux cas. Si une recherche sensible aux cas est nécessaire (par exemple, dans une langue telle que le Cmd où les noms sont sensibles aux cas), utilisez [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Voir aussi
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
