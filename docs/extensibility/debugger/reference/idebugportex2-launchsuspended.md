---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5166e63244d8f437460136b4c116ac148f029919
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876953"
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
  
#### <a name="parameters"></a>Paramètres  
 `pszExe`  
 [in] Le nom de l’exécutable à lancer. Cela peut être un chemin d’accès complet ou un relatif au répertoire de travail spécifié dans le `pszDir` paramètre.  
  
 `pszArgs`  
 [in] Arguments à passer à l’exécutable. Peut-être une valeur null s’il en existe aucun argument.  
  
 `pszDir`  
 [in] Le nom du répertoire de travail utilisé par l’exécutable. Peut-être une valeur null si aucun répertoire de travail n’est requis.  
  
 `bstrEnv`  
 [in] Bloc d’environnement de chaînes se terminant par null, suivie d’un terminateur NULL supplémentaire.  
  
 `hStdInput`  
 [in] Handle vers un autre flux d’entrée. Peut-être 0 si la redirection n’est pas obligatoire.  
  
 `hStdOutput`  
 [in] Handle vers un flux de sortie autre. Peut-être 0 si la redirection n’est pas obligatoire.  
  
 `hStdError`  
 [in] Handle vers un flux de sortie d’erreur alternative. Peut-être 0 si la redirection n’est pas obligatoire.  
  
 `ppPortProcess`  
 [out] Retourne un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objet qui représente le processus lancé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit lancer le processus qu’il est donc suspendue et ne pas en cours d’exécution de code. Le [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) méthode est appelée pour reprendre le processus.  
  
 Un programme peut également être lancé à partir d’un moteur de débogage. Pour plus d’informations, consultez [lancement d’un programme](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Lancement d’un programme](../../../extensibility/debugger/launching-a-program.md)