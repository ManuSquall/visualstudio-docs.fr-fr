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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c08550204c8a2860d8fd7870e4ac949e9e9319c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164199"
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
