---
title: 'IDebugProcessEx2 :: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723397"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Cette méthode ajoute un nœud de programme pour chaque moteur de débogage (DE) spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Paramètres
`guidLaunchingEngine`\
dans `GUID` D’un de qui doit être utilisé pour lancer des programmes (et est supposé ajouter ses propres nœuds de programme).

`rgguidSpecificEngines`\
dans Tableau des ( `GUID` s) pour les nœuds de programme à ajouter.

`celtSpecificEngines`\
dans Nombre de `GUID` s dans le `rgguidSpecificEngines` tableau.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
- Des [nœuds de programme](../../../extensibility/debugger/program-nodes.md) sont ajoutés pour chaque liste dans, à `rgguidSpecificEngines` l’exclusion du moteur de lancement (comme indiqué dans `guidLaunchingEngine` ), qui est supposé ajouter son propre nœud de programme lorsqu’il lance un programme.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nœuds de programme](../../../extensibility/debugger/program-nodes.md)
