---
title: IDebugFunctionObject::CreateObject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728598"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Crée un objet à l’aide d’un constructeur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Paramètres
`pConstructor`\
[dans] Un objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) représentant le constructeur de l’objet à créer.

`dwArgs`\
[dans] Le nombre de paramètres `pArg` dans le tableau. Représente le nombre de paramètres transmis au constructeur.

`pArg`\
[dans] Un tableau d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant les paramètres transmis au constructeur.

`ppObject`\
[out] Retourne `IDebugObject` un représentant de l’objet nouvellement créé.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe (ou tout autre type complexe qui nécessite un constructeur) qui est un paramètre de la fonction qui est représentée par [l’interface IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Si le paramètre de l’objet ne nécessite pas de constructeur, appelez la méthode [CreateObjectNoConstructor.](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
