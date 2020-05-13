---
title: IDebugFunctionObject::CreateObjectNoConstructor (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728578"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Crée un objet sans constructeur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Paramètres
`pClassObject`\
[dans] Un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant le type de l’objet à créer.

`ppObject`\
[out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet nouvellement créé.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente une instance d’une structure ou d’un type complexe (qui ne nécessite pas de constructeur) qui est un paramètre de la fonction qui est représentée par [l’interface IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Si le paramètre de l’objet nécessite un constructeur, appelez la méthode [CreateObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)

## <a name="see-also"></a>Voir aussi
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
