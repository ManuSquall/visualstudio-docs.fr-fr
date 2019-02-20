---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5be03fc6421f03742878f2b72f568ec0915dc
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412914"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtient la classe qui définit cette classe.

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

#### <a name="parameters"></a>Paramètres
`ppClassField`  
[out] Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet représentant la forme de classe. Retourne une valeur null si aucune classe englobante.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Si la classe représentée par ce [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet est une classe imbriquée, puis le `ppClassField` paramètre renvoie un `IDebugClassField` classe d’objet qui représente la forme. Par exemple, étant donné cette définition de classe :

```
class RootClass {
    class NestedClass { }
};
```

Appelant le `GetEnclosingClass` méthode sur le `IDebugClassField` objet représentant le `NestedClass` classe retourne un `IDebugClassField` objet représentant la classe `RootClass`.

## <a name="see-also"></a>Voir aussi
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
