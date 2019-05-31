---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 241db5db55897932120b3253ff5185cb852ea77b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351204"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> DÉCONSEILLÉ. N’UTILISEZ PAS.

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

Une implémentation doit toujours retourner `E_NOTIMPL`.

## <a name="remarks"></a>Notes

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL`.

Cette méthode est appelée lorsque le débogueur se ferme de façon inattendue. Lorsque cette méthode est appelée, l’Allemagne doit reprendre le programme comme si l’utilisateur détachée à partir de celui-ci. Aucun autre événement de débogage ne doit être envoyé. Le programme doit être dans un état où il pouvant être attachée à partir d’une autre instance du débogueur.

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)