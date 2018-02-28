---
title: IDebugProgram3::ExecuteOnThread | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 649b16c1b57b2f66772c2117b776e6b79ad862be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Exécute le programme de débogage. Le thread est retourné afin de donner les informations du débogueur threads sur lesquels l’utilisateur consulte lorsque l’exécution du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Il existe trois façons différentes qu’un débogueur peut reprendre l’exécution après l’arrêt :  
  
-   Exécuter : Annuler une étape précédente et exécuter jusqu'à ce que le point d’arrêt suivant, et ainsi de suite.  
  
-   Étape : Annuler une étape ancien et exécuter jusqu'à la fin de la nouvelle étape.  
  
-   Continuer : Exécutez à nouveau et laisser n’importe quelle étape ancien active.  
  
 Le thread est passé à `ExecuteOnThread` est utile lorsque vous décidez quelle étape d’annulation. Si vous ne connaissez pas le thread en cours d’exécution exécuter annule toutes les étapes. Avec la base de connaissances du thread, vous devez uniquement annuler l’étape sur le thread actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)