---
title: IDebugMethodField::EnumArguments Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727264"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crée un enumérateur pour le type de chaque argument requis pour appeler la méthode.

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
[out] Retourne un objet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des types d’arguments. Retourne une valeur nulle s’il n’y a pas d’arguments.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK ou renvoient S_FALSE s’il n’y a pas d’arguments. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Chaque élément est un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant les types de chaque paramètre. Appelez la méthode [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pour récupérer des informations sur le type de chaque paramètre.

 Si le nom du paramètre est nécessaire avec le type, appelez alors la méthode [EnumParameters.](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
