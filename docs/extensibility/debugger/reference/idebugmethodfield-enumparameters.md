---
title: IDebugMethodField::EnumParameters - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727195"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crée un enumérateur pour les paramètres de la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Paramètres
`ppParams`\
[out] Renvoie un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des paramètres à la méthode; autrement, renvoie une valeur nulle s’il n’y a pas de paramètres.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou retournent S_FALSE s’il n’y a pas de paramètres. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément est un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant différents types de paramètres. Appelez la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) sur chaque objet pour déterminer exactement quel type de paramètre l’objet représente.

 Un paramètre comprend à la fois son nom variable et son type. Le premier paramètre d’une méthode de classe est généralement le pointeur "ce".

 Si seulement les types de paramètres sont nécessaires, appelez la méthode [EnumArguments.](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
