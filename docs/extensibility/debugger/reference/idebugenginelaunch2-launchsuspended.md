---
title: IDebugEngineLaunch2::LaunchSuspended (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730543"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Cette méthode lance un processus au moyen du moteur de débogé (DE).

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
[dans] Le nom de la machine dans laquelle lancer le processus. Utilisez une valeur nulle pour spécifier la machine locale.

`pPort`\
[dans] [L’interface IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) représentant le port dans lequel le programme s’exécutera.

`pszExe`\
[dans] Le nom de l’exécutable à lancer.

`pszArgs`\
[dans] Les arguments à transmettre à l’exécutable. Peut être une valeur nulle s’il n’y a pas d’arguments.

`pszDir`\
[dans] Le nom du répertoire de travail utilisé par l’exécutable. Peut être une valeur nulle si aucun répertoire de travail n’est requis.

`bstrEnv`\
[dans] Bloc environnement des cordes non terminées, suivi d’un terminateur NULL supplémentaire.

`pszOptions`\
[dans] Les options pour l’exécutable.

`dwLaunchFlags`\
[dans] Spécifie le [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) pour une session.

`hStdInput`\
[dans] Gérer à un flux d’entrée alternatif. Peut être 0 si la redirection n’est pas nécessaire.

`hStdOutput`\
[dans] Manipuler à un flux de sortie alternatif. Peut être 0 si la redirection n’est pas nécessaire.

`hStdError`\
[dans] Gérer à un flux de sortie d’erreur alternatif. Peut être 0 si la redirection n’est pas nécessaire.

`pCallback`\
[dans] [L’objet IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui reçoit des événements de débbugger.

`ppDebugProcess`\
[out] Retourne l’objet [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui en résulte qui représente le processus lancé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Normalement, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] lance un programme en utilisant la méthode [LaunchSuspended,](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) puis attache le débbugger au programme suspendu. Cependant, il y a des circonstances dans lesquelles le moteur de débogé peut avoir besoin de lancer un programme (par exemple, si [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] le `IDebugEngineLaunch2::LaunchSuspended` moteur de débogé fait partie d’un interprète et le programme étant débogé est un langage interprété), auquel cas utilise la méthode.

 La méthode [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) est appelée à démarrer le processus après le lancement réussi du processus dans un état suspendu.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
