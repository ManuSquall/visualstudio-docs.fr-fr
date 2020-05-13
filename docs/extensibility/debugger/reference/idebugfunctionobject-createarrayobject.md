---
title: IDebugFunctionObject::CreateArrayObject ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728608"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crée un objet de tableau. Ce tableau peut contenir des valeurs primitives ou d’instance d’objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`ot`\
[dans] Spécifie une valeur du [recensement OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) indiquant le type du nouvel objet de tableau.

`pClassField`\
[dans] Un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant la classe d’un objet, si vous créez un tableau de valeurs d’instance d’objet. Si vous créez une gamme d’objets primitifs, ce paramètre est une valeur nulle.

`dwRank`\
[dans] Le rang ou le nombre de dimensions du tableau.

`dwDims`\
[dans] Les tailles de chaque dimension du tableau.

`dwLowBounds`\
[dans] L’origine de chaque dimension (généralement 0 ou 1).

`ppObject`\
[out] Retourne un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant le tableau nouvellement créé. Il s’agit en fait d’un objet [IDebugArrayObject.](../../../extensibility/debugger/reference/idebugarrayobject.md)

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente un paramètre de tableau à la fonction qui est représentée par [l’interface IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
