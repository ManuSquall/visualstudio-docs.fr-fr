---
title: IDebugProgramNode2::DetachDebugger_V7 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fdf4875c30bebaeed925af57c0d80910f8fcbf21
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> DÉCONSEILLÉE. N’UTILISEZ PAS.

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

Une implémentation doit toujours renvoyer `E_NOTIMPL`.

## <a name="remarks"></a>Notes

> [!WARNING]
> À compter de Visual Studio 2005, cette méthode n’est plus utilisée et doit toujours renvoyer `E_NOTIMPL`.

Cette méthode est appelée lorsque le débogueur se ferme de façon inattendue. Lorsque cette méthode est appelée, le DE reprendre le programme comme si l’utilisateur détachée à partir de celui-ci. Plus aucun événement de débogage ne doit être envoyé. Le programme doit être dans un état où il pouvant être attaché à partir d’une autre instance du débogueur.

## <a name="see-also"></a>Voir aussi

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)