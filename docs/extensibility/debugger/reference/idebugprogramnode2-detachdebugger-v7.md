---
title: IDebugProgramNode2::DetachDebugger-V7 ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722107"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Déconseillée. NE PAS UTILISER.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valeur de retour

Une mise en `E_NOTIMPL`œuvre doit toujours revenir .

## <a name="remarks"></a>Notes

> [!WARNING]
> A partir de Visual Studio 2005, cette méthode `E_NOTIMPL`n’est plus utilisée et devrait toujours revenir .

Cette méthode est appelée lorsque le débbuggeur quitte de façon inattendue. Lorsque cette méthode est appelée, le DE doit reprendre le programme comme si l’utilisateur s’en était détaché. Il ne faut plus envoyer d’événements de débogé. Le programme devrait être dans un état où il est joignable d’un autre cas du débbuggeur.

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
