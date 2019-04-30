---
title: IDebugMethodField::EnumArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf62392118ed3ddfb2dfbfca06588f0935f3192d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918722"
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

#### <a name="parameters"></a>Paramètres
 `ppParams`

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