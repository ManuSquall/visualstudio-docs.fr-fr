---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ee2a93f10aa912ba1619342d814817c8abd5307
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504099"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugPortEx2::LaunchSuspended](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportex2-launchsuspended).  
  
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

