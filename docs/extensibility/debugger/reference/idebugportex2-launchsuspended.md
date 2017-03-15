---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

lance un fichier exécutable.  
  
## Syntaxe  
  
```cpp#  
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
  
```c#  
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
  
#### Paramètres  
 `pszExe`  
 \[in\]  Le nom du fichier exécutable à démarrer.  Il peut s'agir d'un chemin d'accès complet ou relatif au répertoire de travail spécifié dans le paramètre d' `pszDir` .  
  
 `pszArgs`  
 \[in\]  les arguments à passer au fichier exécutable.  Peut être une valeur NULL si aucun argument n'est spécifié.  
  
 `pszDir`  
 \[in\]  le nom du répertoire de travail utilisé par le fichier exécutable.  peut être une valeur NULL si aucun répertoire de travail n'est requis.  
  
 `bstrEnv`  
 \[in\]  Bloc environnement de chaînes terminée par le caractère NULL, suivi d'une marque de fin null supplémentaire.  
  
 `hStdInput`  
 \[in\]  Handle vers un autre flux d'entrée.  peut être 0 si la redirection n'est pas requise.  
  
 `hStdOutput`  
 \[in\]  Handle vers un autre flux de sortie.  peut être 0 si la redirection n'est pas requise.  
  
 `hStdError`  
 \[in\]  Handle vers un autre flux de sortie des erreurs.  peut être 0 si la redirection n'est pas requise.  
  
 `ppPortProcess`  
 \[out\]  Retourne un objet d' [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) qui représente le processus exécuté.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode doit exécuter le processus afin qu'elle soit interrompue et n'est pas en cours de exécution du code.  La méthode d' [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) est appelée pour reprendre le processus.  
  
 un programme peut également être lancé d'un moteur de débogage.  Pour plus d'informations, consultez [Lancement d'un programme](../../../extensibility/debugger/launching-a-program.md).  
  
## Voir aussi  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Lancement d'un programme](../../../extensibility/debugger/launching-a-program.md)