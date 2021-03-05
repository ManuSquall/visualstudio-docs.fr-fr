---
description: Met fin au programme.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 880bf4e727d90c19cf11f42cc3020124235bb1e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171981"
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
