---
description: Crée un objet à l’aide d’un constructeur.
title: 'IDebugFunctionObject :: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27608634859ae96a8fb9461076397bb6df53570d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073558"
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
dans Objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) qui représente le constructeur de l’objet à créer.

`dwArgs`\
dans Nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres passés au constructeur.

`pArg`\
dans Tableau d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant les paramètres passés au constructeur.

`ppObject`\
à Retourne un `IDebugObject` qui représente l’objet nouvellement créé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe (ou un autre type complexe qui requiert un constructeur) qui est un paramètre de la fonction qui est représenté par l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Si le paramètre d’objet ne requiert pas de constructeur, appelez la méthode [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
