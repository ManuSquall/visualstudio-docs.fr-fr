---
title: IDebugPortEx2:LaunchSuspended (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725096"
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
[dans] Le nom de l’exécutable à lancer. Il peut s’agir d’un chemin complet `pszDir` ou d’un parcours par rapport à l’annuaire de travail spécifié dans le paramètre.

`pszArgs`\
[dans] Les arguments à transmettre à l’exécutable. Peut être une valeur nulle s’il n’y a pas d’arguments.

`pszDir`\
[dans] Le nom du répertoire de travail utilisé par l’exécutable. Peut être une valeur nulle si aucun répertoire de travail n’est requis.

`bstrEnv`\
[dans] Bloc de l’environnement des cordes non terminées, suivie d’un terminateur NULL supplémentaire.

`hStdInput`\
[dans] Gérer à un flux d’entrée alternatif. Peut être 0 si la redirection n’est pas nécessaire.

`hStdOutput`\
[dans] Manipuler à un flux de sortie alternatif. Peut être 0 si la redirection n’est pas nécessaire.

`hStdError`\
[dans] Gérer à un flux de sortie d’erreur alternatif. Peut être 0 si la redirection n’est pas nécessaire.

`ppPortProcess`\
[out] Retourne un objet [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le processus lancé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode doit lancer le processus afin qu’il soit suspendu et ne pas exécuter de code. La méthode [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) est appelée à reprendre le processus.

 Un programme peut également être lancé à partir d’un moteur de débogé. Pour plus de détails, voir [Lancement d’un programme](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Voir aussi
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Lancement d’un programme](../../../extensibility/debugger/launching-a-program.md)
