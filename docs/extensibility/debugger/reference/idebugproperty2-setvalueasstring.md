---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27b481165cf95a97d7674d52d8553426dfb6417c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314607"
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