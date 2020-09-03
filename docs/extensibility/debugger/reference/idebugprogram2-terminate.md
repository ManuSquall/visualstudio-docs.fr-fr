---
title: 'IDebugProgram2 :: Terminate | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722746"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Met fin au programme.

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
 Si possible, le programme sera arrêté et déchargé du processus. dans le cas contraire, le moteur DE débogage (DE) effectue tout nettoyage nécessaire.

 Cette méthode ou la méthode [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) est appelée par l’IDE, généralement en réponse à l’arrêt de tout débogage par l’utilisateur. L’implémentation de cette méthode doit, dans l’idéal, terminer le programme au sein du processus. Si ce n’est pas possible, le DE doit empêcher le programme de s’exécuter plus dans ce processus (et effectuer tout nettoyage nécessaire). Si la `IDebugProcess2::Terminate` méthode a été appelée par l’IDE, le processus entier se termine quelque temps après l’appel de la `IDebugProgram2::Terminate` méthode.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminer](../../../extensibility/debugger/reference/idebugprocess2-terminate.md).
