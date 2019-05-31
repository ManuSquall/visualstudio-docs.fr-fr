---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d455d380f66689cd2245070a7ef0bf9290a2455
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324218"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crée un énumérateur pour les paramètres de la méthode.

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
[out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des paramètres à la méthode de l’objet ; sinon, retourne une valeur null si aucun paramètre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il n’existe aucun paramètre. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément est un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant les différents types de paramètres. Appelez le [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) méthode sur chaque objet pour déterminer exactement quel type de paramètre de l’objet représente.

 Un paramètre inclut son nom de la variable et son type. Le premier paramètre à une méthode de classe est généralement le pointeur « this ».

 Si seuls les types des paramètres est nécessaire, appelez le [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)