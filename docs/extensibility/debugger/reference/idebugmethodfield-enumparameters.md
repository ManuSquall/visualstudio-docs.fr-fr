---
title: 'IDebugMethodField :: EnumParameters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c164fa08f4195d685bf7dd2faa120ff030e44c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837721"
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
à Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des paramètres de la méthode. Sinon, retourne une valeur null s’il n’y a aucun paramètre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ou retourne S_FALSE s’il n’y a aucun paramètre. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Chaque élément est un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant différents types de paramètres. Appelez la méthode [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) sur chaque objet pour déterminer exactement le type de paramètre représenté par l’objet.

 Un paramètre comprend à la fois son nom de variable et son type. Le premier paramètre d’une méthode de classe est généralement le pointeur « this ».

 Si seuls les types des paramètres sont nécessaires, appelez la méthode [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
