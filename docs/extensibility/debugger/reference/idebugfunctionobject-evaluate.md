---
description: 'IDebugFunctionObject :: Evaluate appelle la fonction et retourne la valeur résultante sous la forme d’un objet.'
title: 'IDebugFunctionObject :: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d15cdb09de32edcdf6159567db12e05cffd06e7e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160106"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Appelle la fonction et retourne la valeur résultante sous la forme d’un objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Paramètres
`ppParams`\
dans Tableau d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant les paramètres d’entrée. Chacun de ces paramètres a été créé avec l’une des `Create` méthodes de l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

`dwParams`\
dans Nombre de paramètres dans le `ppParams` tableau.

`dwTimeout`\
dans Spécifie la durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`ppResult`\
à Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant la valeur de la fonction sous la forme d’un objet.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode configure et exécute un appel à la fonction représentée par l’objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
