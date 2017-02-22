---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode exécute un processus à l'aide de le moteur de \(DE\) débogage.  
  
## Syntaxe  
  
```cpp#  
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
  
```c#  
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
  
#### Paramètres  
 `pszMachine`  
 \[in\]  Le nom de l'ordinateur dans lequel exécuter le processus.  Utilisez une valeur NULL pour spécifier l'ordinateur local.  
  
 `pPort`  
 \[in\]  L'interface d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) représentant le port dans lequel le programme s'exécute.  
  
 `pszExe`  
 \[in\]  Le nom du fichier exécutable à démarrer.  
  
 `pszArgs`  
 \[in\]  les arguments à passer au fichier exécutable.  Peut être une valeur NULL si aucun argument n'est spécifié.  
  
 `pszDir`  
 \[in\]  le nom du répertoire de travail utilisé par le fichier exécutable.  peut être une valeur NULL si aucun répertoire de travail n'est requis.  
  
 `bstrEnv`  
 \[in\]  Bloc environnement de chaînes terminée par le caractère NULL, suivi d'une marque de fin null supplémentaire.  
  
 `pszOptions`  
 \[in\]  les options pour le fichier exécutable.  
  
 `dwLaunchFlags`  
 \[in\]  spécifie [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) pour une session.  
  
 `hStdInput`  
 \[in\]  Handle vers un autre flux d'entrée.  peut être 0 si la redirection n'est pas requise.  
  
 `hStdOutput`  
 \[in\]  Handle vers un autre flux de sortie.  peut être 0 si la redirection n'est pas requise.  
  
 `hStdError`  
 \[in\]  Handle vers un autre flux de sortie des erreurs.  peut être 0 si la redirection n'est pas requise.  
  
 `pCallback`  
 \[in\]  l'objet d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui reçoit des événements de débogueur.  
  
 `ppDebugProcess`  
 \[out\]  Retourne l'objet résultant d' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) qui représente le processus exécuté.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Normalement, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] exécute un programme à l'aide de la méthode d' [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) puis joint le débogueur au programme suspendu.  Toutefois, il existe des situations dans lesquelles le moteur de débogage peut devoir exécuter un programme \(par exemple, si le moteur de débogage fait partie d'un interpréteur et du programme débogué est un langage interprète\), auquel cas [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utilise la méthode d' `IDebugEngineLaunch2::LaunchSuspended` .  
  
 La méthode d' [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) est appelée pour démarrer le processus une fois que le processus a été correctement lancé dans un état suspendu.  
  
## Voir aussi  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)