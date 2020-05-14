---
title: IDebugProgram2::Terminate Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722746"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termine le programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Si possible, le programme sera résilié et déchargé du processus; sinon, le moteur de débogé (DE) effectuera tout nettoyage nécessaire.

 Cette méthode ou la méthode [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) est appelée par l’IDE, généralement en réponse à l’utilisateur arrêtant tout débogage. La mise en œuvre de cette méthode devrait, idéalement, mettre fin au programme dans le cadre du processus. Si cela n’est pas possible, le DE devrait empêcher le programme de fonctionner plus dans ce processus (et faire tout nettoyage nécessaire). Si `IDebugProcess2::Terminate` la méthode a été appelée par l’IDE, `IDebugProgram2::Terminate` l’ensemble du processus sera terminé quelque temps après l’appel de la méthode.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
