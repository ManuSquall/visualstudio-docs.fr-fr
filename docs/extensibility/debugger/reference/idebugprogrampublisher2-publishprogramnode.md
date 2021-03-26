---
description: Rend un nœud de programme disponible pour une utilisation par les moteurs de débogage (DEs) et le gestionnaire de débogage de session (SDM).
title: IDebugProgramPublisher2 ::P ublishProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62de2e91d9331d33e40e6364893850d40f8e8eca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065149"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Rend un nœud de programme disponible pour une utilisation par les moteurs de débogage (DEs) et le gestionnaire de débogage de session (SDM).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Paramètres
`pProgramNode`\
dans Objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le nœud de programme à rendre disponible.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode permet aux programmes d’effectuer des requêtes d’informations avant de les sélectionner et de les lancer pour le débogage.

 Pour supprimer un nœud de programme de la disponibilité, appelez la méthode [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
