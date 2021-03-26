---
description: Obtient le pointeur this (me dans Visual Basic) de l’objet contenant la méthode.
title: 'IDebugMethodField :: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 662555ec4552aa016b40c1e9c8222992e6cdfd66
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076639"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtient le `this` `Me` pointeur (en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) de l’objet contenant la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Paramètres
`ppClass`\
à Retourne un objet [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) qui représente le pointeur « this ».

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Dans les langages orientés objet, il existe généralement un pointeur implicite vers l’instanciation actuelle d’une classe. Cela est connu sous le nom `this` de C#/c + + et comme `Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
