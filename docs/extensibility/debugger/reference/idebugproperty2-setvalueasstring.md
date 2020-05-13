---
title: IDebugProperty2::SetValueAsString (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721243"
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
[dans] Une chaîne contenant la valeur à définir.

`nRadix`\
[dans] Un radix à utiliser pour interpréter toute information numérique. Cela peut être 0 pour tenter de déterminer le radix automatiquement.

`dwTimeout`\
[dans] Spécifie le temps maximum, en millisecondes, d’attendre avant de revenir de cette méthode. Utilisez-le `INFINITE` pour attendre indéfiniment.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur. Le tableau suivant montre d’autres valeurs possibles.

|Valeur|Description|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La chaîne ne pouvait pas être convertie en valeur de propriété, ou la valeur de la propriété ne pouvait pas être définie.|
|`E_SETVALUE_VALUE_IS_READONLY`|la propriété est en lecture seule.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
