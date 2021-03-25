---
description: Cette méthode lance un processus au moyen du moteur de débogage (DE).
title: 'IDebugEngineLaunch2 :: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2db2ce2a35cd8be6599fca3e01bc69a6680012b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066020"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Cette méthode lance un processus au moyen du moteur de débogage (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Paramètres
`pszMachine`\
dans Nom de la machine dans laquelle lancer le processus. Utilisez une valeur null pour spécifier l’ordinateur local.

`pPort`\
dans Interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) représentant le port dans lequel le programme s’exécutera.

`pszExe`\
dans Nom de l’exécutable à lancer.

`pszArgs`\
dans Arguments à passer à l’exécutable. Peut être une valeur null s’il n’y a pas d’arguments.

`pszDir`\
dans Nom du répertoire de travail utilisé par l’exécutable. Peut être une valeur null si aucun répertoire de travail n’est requis.

`bstrEnv`\
dans Bloc d’environnement de chaînes terminées par un caractère NULL, suivi d’une marque de fin NULL supplémentaire.

`pszOptions`\
dans Options pour l’exécutable.

`dwLaunchFlags`\
dans Spécifie les [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) pour une session.

`hStdInput`\
dans Handle vers un autre flux d’entrée. Peut avoir la valeur 0 si la redirection n’est pas nécessaire.

`hStdOutput`\
dans Handle vers un autre flux de sortie. Peut avoir la valeur 0 si la redirection n’est pas nécessaire.

`hStdError`\
dans Handle vers un autre flux de sortie d’erreur. Peut avoir la valeur 0 si la redirection n’est pas nécessaire.

`pCallback`\
dans Objet [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui reçoit les événements du débogueur.

`ppDebugProcess`\
à Retourne l’objet [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) résultant qui représente le processus lancé.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Normalement, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] lance un programme à l’aide de la méthode [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) , puis attache le débogueur au programme suspendu. Toutefois, dans certains cas, le moteur de débogage peut avoir besoin de lancer un programme (par exemple, si le moteur de débogage fait partie d’un interpréteur et si le programme en cours de débogage est un langage interprété), auquel cas [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utilise la `IDebugEngineLaunch2::LaunchSuspended` méthode.

 La méthode [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) est appelée pour démarrer le processus une fois que le processus a été lancé avec succès dans un état suspendu.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
