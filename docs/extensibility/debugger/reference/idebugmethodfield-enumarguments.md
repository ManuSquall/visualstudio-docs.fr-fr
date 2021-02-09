---
title: 'IDebugMethodField :: EnumArguments | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b86fbdb87c0191ea8b43c64a542c37177a8ef1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900194"
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
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des types d’arguments. Retourne une valeur null s’il n’y a pas d’arguments.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a pas d’arguments. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Chaque élément est un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui représente les types de chaque paramètre. Appelez la méthode [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pour récupérer des informations sur le type de chaque paramètre.

 Si le nom du paramètre est requis avec le type, appelez la méthode [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
