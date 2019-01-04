---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbb2650fc2c001e57de7b1820cff238c8963e8cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889434"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Exécute le programme de débogueur. Le thread est retourné pour fournir les informations du débogueur threads sur lesquels l’utilisateur consulte lorsque l’exécution du programme.  
  
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
  
- Exécutez : Annuler toutes les étapes précédentes et exécuter jusqu'à ce que le point d’arrêt suivant, et ainsi de suite.  
  
- Étape : Annulez toute étape ancien et exécuter jusqu'à la fin de la nouvelle étape.  
  
- Continuer : Exécutez à nouveau et laisser une étape quelconque ancien active.  
  
  Le thread est passé à `ExecuteOnThread` est utile lorsque vous décidez quelle étape d’annulation. Si vous ne connaissez pas le thread en cours d’exécution exécuter annule toutes les étapes. Avec les connaissances du thread, il vous suffit d’annuler l’étape sur le thread actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)