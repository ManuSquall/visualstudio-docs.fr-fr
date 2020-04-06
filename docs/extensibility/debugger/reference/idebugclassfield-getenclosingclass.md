---
title: IDebugClassField::GetEnclosingClass (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734397"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtient la classe qui entoure cette classe.

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
[out] Retourne un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant la classe d’enceinte. Renvoie une valeur nulle s’il n’y a pas de classe d’enceinte.

## <a name="return-value"></a>Valeur de retour
En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
Si la classe représentée par cet objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) est `ppClassField` une `IDebugClassField` classe imbriquée, le paramètre renvoie un objet représentant la classe d’enceinte. Par exemple, compte tenu de cette définition de classe :

```
class RootClass {
    class NestedClass { }
};
```

Appeler `GetEnclosingClass` la méthode `IDebugClassField` sur `NestedClass` l’objet `IDebugClassField` représentant la `RootClass`classe renvoie un objet représentant la classe .

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
