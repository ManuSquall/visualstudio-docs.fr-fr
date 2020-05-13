---
title: IDebugQueryEngine2::GetEngineInterface (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82f3214783a35e668bf3164c8659f60f863e9a43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720662"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Obtient une interface personnalisée de moteur de débogé (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Paramètres
`ppUnk`\
[out] Retourne `IUnknown` un objet représente le moteur de débogé (DE), et qui peut être interrogé pour toute autre interface valide associée à un DE (par exemple [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) ou [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’interface résultante doit être utilisée avec soin parce que l’appel à travers les interfaces récupérées à partir de cette méthode contourne le traitement du gestionnaire de déboguer la session et peut entraîner le SDM entrer dans un mauvais état ou générer des erreurs tout en débogage.

## <a name="see-also"></a>Voir aussi
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
