---
title: IDebugMethodField::EnumArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0c5f95267948b6fb2c1cab1a7d79a2e62b9e3c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346783"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Paramètres
`ppParams`\
[out] Retourne un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objet représentant la liste des types d’arguments. Retourne une valeur null s’il en existe aucun argument.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK, ou retourne S_FALSE s’il y a aucun argument. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément est un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant les types de chaque paramètre. Appelez le [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) méthode pour récupérer des informations sur le type de chaque paramètre.

 Si le nom du paramètre est nécessaire, ainsi que le type, puis appelez le [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)