---
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e9b6447827baa80da2843c992a8d2233dd1a4b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949407"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère une liste de tous les threads en cours d’exécution dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppEnum`  
 [out] Retourne un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) objet qui contient une liste de tous les threads dans tous les programmes dans le processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode énumère les threads en cours d’exécution dans chaque programme et les combine ensuite en une vue des threads de processus. Un seul thread peut exécuter plusieurs programmes. Cette méthode énumère une seule fois ce thread.  
  
 Cette méthode présente une liste de threads du processus sans doublons. Sinon, pour énumérer les threads en cours d’exécution dans un programme particulier, utilisez le [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
