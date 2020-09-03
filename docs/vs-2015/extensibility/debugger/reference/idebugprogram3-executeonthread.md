---
title: 'IDebugProgram3 :: ExecuteOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfc64f8ae928b4bb0057a16b8a74c6ddbff588c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148633"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Exécute le programme du débogueur. Le thread est retourné pour fournir les informations du débogueur sur le thread affiché par l’utilisateur lors de l’exécution du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThread`  
 dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Il existe trois façons différentes de reprendre l’exécution d’un débogueur après l’arrêt :  
  
- Exécuter : annuler toute étape précédente et exécuter jusqu’au point d’arrêt suivant, et ainsi de suite.  
  
- Étape : annulez toute ancienne étape et exécutez jusqu’à ce que la nouvelle étape soit terminée.  
  
- Continuer : réexécutez et laissez l’ancienne étape active.  
  
  Le thread passé à `ExecuteOnThread` est utile pour décider de l’étape à annuler. Si vous ne connaissez pas le thread, l’exécution de l’instruction EXECUTE Annule toutes les étapes. Avec la connaissance du thread, il vous suffit d’annuler l’étape sur le thread actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectue](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
