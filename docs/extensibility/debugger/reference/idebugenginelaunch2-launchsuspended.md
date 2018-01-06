---
title: IDebugEngineLaunch2::LaunchSuspended | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords: IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b9c05a566c62df63ebabebab287188011e4f1ca5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Paramètres  
 `pszMachine`  
 [in] Le nom de l’ordinateur permettant de lancer le processus. Pour spécifier l’ordinateur local, utilisez une valeur null.  
  
 `pPort`  
 [in] Le [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface qui représente le port que le programme s’exécutera dans.  
  
 `pszExe`  
 [in] Le nom de l’exécutable à lancer.  
  
 `pszArgs`  
 [in] Arguments à passer à l’exécutable. Peut-être une valeur null s’il n’existe aucun argument.  
  
 `pszDir`  
 [in] Le nom du répertoire de travail utilisé par le fichier exécutable. Peut-être une valeur null si aucun répertoire de travail n’est nécessaire.  
  
 `bstrEnv`  
 [in] Bloc d’environnement de chaînes se terminant par NULL, suivi d’un terminateur NULL supplémentaire.  
  
 `pszOptions`  
 [in] Les options pour le fichier exécutable.  
  
 `dwLaunchFlags`  
 [in] Spécifie le [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) pour une session.  
  
 `hStdInput`  
 [in] Handle vers un autre flux d’entrée. Peut-être 0 si la redirection n’est pas nécessaire.  
  
 `hStdOutput`  
 [in] Handle vers un flux de sortie de remplacement. Peut-être 0 si la redirection n’est pas nécessaire.  
  
 `hStdError`  
 [in] Handle vers un flux de sortie d’erreur secondaire. Peut-être 0 si la redirection n’est pas nécessaire.  
  
 `pCallback`  
 [in] Le [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet qui reçoit des événements de débogueur.  
  
 `ppDebugProcess`  
 [out] Retourne la qui en résulte [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet qui représente le processus lancé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Normalement, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] lance un programme à l’aide de la [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) (méthode), puis l’attache le débogueur au programme interrompu. Toutefois, il existe des circonstances dans lesquelles le moteur de débogage devrez peut-être lancer un programme (par exemple, si le moteur de débogage fait partie d’un interpréteur et le programme débogué est un langage interprété), auquel cas [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utilise le `IDebugEngineLaunch2::LaunchSuspended` (méthode) .  
  
 Le [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) méthode est appelée pour démarrer le processus une fois que le processus a été lancé avec succès dans un état suspendu.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)