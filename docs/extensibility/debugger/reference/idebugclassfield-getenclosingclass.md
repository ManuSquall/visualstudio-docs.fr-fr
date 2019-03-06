---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 9e6b2cfae694d0d95f70b2251efc66764df1b539
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682009"
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
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
