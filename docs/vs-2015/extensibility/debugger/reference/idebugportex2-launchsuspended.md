---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947727"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Lance un fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
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
