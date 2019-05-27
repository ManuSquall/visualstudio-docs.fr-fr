---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba8a7ab97c9b2fc405e10eb70246a049b4083993
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200217"
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
[in] Chaîne contenant la valeur à définir.

`nRadix`\
[in] Une base pour être utilisées pour interpréter toutes les informations numériques. Cela peut être 0 pour tenter de déterminer la base automatiquement.

`dwTimeout`\
[in] Spécifie la durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Le tableau suivant présente les autres valeurs possibles.

|Value|Description|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La chaîne n’a pas pu être convertie en une valeur de propriété, ou la valeur de propriété pas pu être définie.|
|`E_SETVALUE_VALUE_IS_READONLY`|La propriété doit être en lecture seule.|

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)