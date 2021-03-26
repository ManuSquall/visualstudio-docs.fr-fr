---
description: Obtient la classe qui englobe cette classe.
title: 'IDebugClassField :: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c59eb2559634c67b210f4fc3b4ce41743346c8ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088482"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtient la classe qui englobe cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Paramètres
`ppClassField`\
à Retourne un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant la classe englobante. Retourne une valeur null s’il n’existe aucune classe englobante.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Si la classe représentée par cet objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) est une classe imbriquée, le `ppClassField` paramètre retourne un `IDebugClassField` objet représentant la classe englobante. Par exemple, à partir de cette définition de classe :

```
class RootClass {
    class NestedClass { }
};
```

L’appel `GetEnclosingClass` de la méthode sur l' `IDebugClassField` objet représentant la `NestedClass` classe retourne un `IDebugClassField` objet représentant la classe `RootClass` .

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
