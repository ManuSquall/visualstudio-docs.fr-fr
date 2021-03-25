---
description: Cette méthode récupère l’exception associée à un objet, le cas échéant.
title: 'IDebugBinder3 :: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67f6c146182546f83782a0299c0ea3e29f94a3b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094248"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Cette méthode récupère l’exception associée à un objet, le cas échéant.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Paramètres
`ppException`\
à Retourne l’objet représentant l’exception.

`ppField`\
à Retourne l’objet représentant un champ spécifique qui peut avoir provoqué l’exception (il peut s’agir d’une valeur null).

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

> [!NOTE]
> Pour vérifier s’il existe une exception, vérifiez la valeur retournée par `ppException` : s’il s’agit d’une valeur null, aucune exception n’est associée à cet objet.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
