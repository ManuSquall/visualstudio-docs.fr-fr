---
title: IDebugMethodField::EnumStaticLocals ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727157"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Crée un enumérateur pour les variables locales statiques de la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Paramètres
`ppLocals`\
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des habitants statiques. Retourne une valeur nulle s’il n’y a pas d’habitants statiques.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, retourne S_OK ou retourne S_FALSE s’il n’y a pas d’habitants statiques. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément est un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant différents types d’habitants statiques. Appelez la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) sur chaque objet pour déterminer exactement quel type de local statique l’objet représente.

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
