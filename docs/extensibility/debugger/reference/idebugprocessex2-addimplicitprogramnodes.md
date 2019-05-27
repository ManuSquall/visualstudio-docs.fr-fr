---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 411b0b40d6c47f240472c82f727d955dda8df2df
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204090"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Cette méthode ajoute un nœud de programme pour chaque moteur de débogage (dé) spécifié.

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
[in] Le `GUID` d’un type de données DE qui doit être utilisée pour lancer des programmes (et est supposé pour ajouter des nœuds de son propre programme).

`rgguidSpecificEngines`\
[in] Tableau de `GUID`s DEs quel programme nœuds seront ajoutés.

`celtSpecificEngines`\
[in] Le nombre de `GUID`s dans le `rgguidSpecificEngines` tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
- [Programmer des nœuds](../../../extensibility/debugger/program-nodes.md) sera ajouté pour chaque dé répertoriées dans `rgguidSpecificEngines`, à l’exclusion du moteur de lancement (selon les indications dans `guidLaunchingEngine`), qui est censé pour ajouter son propre nœud de programme lors du lancement d’un programme.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nœuds de programme](../../../extensibility/debugger/program-nodes.md)