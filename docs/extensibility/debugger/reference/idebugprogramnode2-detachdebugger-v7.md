---
title: IDebugProgramNode2 ::D etachDebugger_V7 | Microsoft Docs
description: Cette méthode est une forme ancienne et déconseillée de la méthode de détachement utilisée avant Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16630be49dd884f8bcc82da2fead158eb3a25e5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053553"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Déconseillé. N’UTILISEZ PAS.

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

Une implémentation doit toujours retourner `E_NOTIMPL` .

## <a name="remarks"></a>Notes

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL` .

Cette méthode est appelée lorsque le débogueur se ferme de manière inattendue. Lorsque cette méthode est appelée, le DE doit reprendre le programme comme si l’utilisateur l’avait détaché. Aucun autre événement de débogage ne doit être envoyé. Le programme doit être dans un État où il peut être attaché à partir d’une autre instance du débogueur.

## <a name="see-also"></a>Voir aussi

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
