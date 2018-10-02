---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ad46418897f4cdd2521209dd6643362e81bfcb6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505242"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugProgram3::ExecuteOnThread](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram3-executeonthread).  
  
Exécute le programme de débogueur. Le thread est retourné pour fournir les informations du débogueur threads sur lesquels l’utilisateur consulte lorsque l’exécution du programme.  
  
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
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Il existe trois façons différentes qu’un débogueur peut reprendre l’exécution après l’arrêt :  
  
-   Exécuter : Annuler toutes les étapes précédentes et exécuter jusqu'à ce que le point d’arrêt suivant, et ainsi de suite.  
  
-   Étape : Annuler une étape quelconque ancien et exécuter jusqu'à la fin de la nouvelle étape.  
  
-   Continuer : Exécutez à nouveau et laisser une étape quelconque ancien active.  
  
 Le thread est passé à `ExecuteOnThread` est utile lorsque vous décidez quelle étape d’annulation. Si vous ne connaissez pas le thread en cours d’exécution exécuter annule toutes les étapes. Avec les connaissances du thread, il vous suffit d’annuler l’étape sur le thread actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

