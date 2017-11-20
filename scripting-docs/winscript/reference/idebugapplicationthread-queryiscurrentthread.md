---
title: IDebugApplicationThread::QueryIsCurrentThread | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a291005a7c5b85230c55c736c68de82c0290d0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Détermine si ce thread est le thread en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi, et c’est le thread en cours d’exécution.|  
|`S_FALSE`|Ce n’est pas le thread en cours d’exécution.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode détermine si ce thread est le thread en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)