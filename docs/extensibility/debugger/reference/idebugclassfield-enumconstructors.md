---
title: IDebugClassField:EnumConstructors Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734458"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crée un enumérateur pour les constructeurs pour cette classe.

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
[dans] Une valeur de [l’énumération CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) qui spécifie le type de constructeurs à l’énumération.

`ppEnum`\
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des constructeurs. Retourne une valeur nulle s’il n’y a pas de constructeurs.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou retournent S_FALSE s’il n’y a pas de constructeurs. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément de l’énumération est un objet [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) décrivant une méthode de constructeur.

 La liste des constructeurs n’inclut généralement pas les constructeurs par défaut fournis par un compilateur.

## <a name="see-also"></a>Voir aussi
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
