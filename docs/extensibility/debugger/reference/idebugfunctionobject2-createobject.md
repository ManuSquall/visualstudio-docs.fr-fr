---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23380106a1c78ba139beec94698bcfa5090c4b08
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200744"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crée un objet qui utilise un constructeur étant donné les paramètres de l’indicateur d’évaluation et une valeur de délai d’attente.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Paramètres
`pConstructor`\
[in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet qui représente le constructeur de l’objet doit être créé.

`dwArgs`\
[in] Le nombre de paramètres dans le `pArg` tableau. Représente le nombre de paramètres passés au constructeur.

`pArgs`\
[in] Un tableau de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) les objets qui représente les paramètres passés au constructeur.

`dwEvalFlags`\
[in] Une combinaison d’indicateurs de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifient la façon dont l’évaluation doit être effectuée.

`dwTimeout`\
[in] Durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez **infinie** pour attendre indéfiniment.

`ppObject`\
[out] Retourne un **IDebugObject** représentant l’objet nouvellement créé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Appelez cette méthode pour créer un objet qui représente une instance d’une classe ou autre type complexe qui nécessite un constructeur, qui est un paramètre.

## <a name="see-also"></a>Voir aussi
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)