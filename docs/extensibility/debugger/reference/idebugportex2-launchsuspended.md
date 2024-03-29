---
description: Lance un fichier exécutable.
title: 'IDebugPortEx2 :: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fdffb6f87285e9f33d6abaf864b4d45345a304ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072492"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Lance un fichier exécutable.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Paramètres
`pszExe`\
dans Nom de l’exécutable à lancer. Il peut s’agir d’un chemin d’accès complet ou relatif au répertoire de travail spécifié dans le `pszDir` paramètre.

`pszArgs`\
dans Arguments à passer à l’exécutable. Peut être une valeur null s’il n’y a pas d’arguments.

`pszDir`\
dans Nom du répertoire de travail utilisé par l’exécutable. Peut être une valeur null si aucun répertoire de travail n’est requis.

`bstrEnv`\
dans Bloc d’environnement de chaînes terminées par un caractère null, suivi d’une marque de fin NULL supplémentaire.

`hStdInput`\
dans Handle vers un autre flux d’entrée. Peut avoir la valeur 0 si la redirection n’est pas nécessaire.

`hStdOutput`\
dans Handle vers un autre flux de sortie. Peut avoir la valeur 0 si la redirection n’est pas nécessaire.

`hStdError`\
dans Handle vers un autre flux de sortie d’erreur. Peut avoir la valeur 0 si la redirection n’est pas nécessaire.

`ppPortProcess`\
à Retourne un objet [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le processus lancé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode doit lancer le processus afin qu’il soit suspendu et n’exécute aucun code. La méthode [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) est appelée pour reprendre le processus.

 Un programme peut également être lancé à partir d’un moteur de débogage. Pour plus d’informations, consultez [lancement d’un programme](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Voir aussi
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Lancement d’un programme](../../../extensibility/debugger/launching-a-program.md)
