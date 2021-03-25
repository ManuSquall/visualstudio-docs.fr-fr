---
description: Crée un énumérateur pour les constructeurs pour cette classe.
title: 'IDebugClassField :: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8efba9ecb25259b6aa4998a1f22fedf443c1281a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084972"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crée un énumérateur pour les constructeurs pour cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Paramètres
`cMatch`\
dans Valeur de l’énumération [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) qui spécifie le type de constructeurs à énumérer.

`ppEnum`\
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des constructeurs. Retourne une valeur null s’il n’existe aucun constructeur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a aucun constructeur. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément de l’énumération est un objet [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) décrivant une méthode de constructeur.

 En général, la liste des constructeurs n’inclut pas les constructeurs par défaut fournis par un compilateur.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
