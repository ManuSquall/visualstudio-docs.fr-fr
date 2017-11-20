---
title: IRemoteDebugApplication::QueryAlive | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.QueryAlive
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::QueryAlive
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f938ad30562cd1131e8a50077106002d33cea2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationqueryalive"></a>IRemoteDebugApplication::QueryAlive
Indique si l’application ne répond.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode indique si l’application ne répond. Les implémentations de cette méthode doivent toujours retourner `S_OK`.  
  
 Si le processus d’application se termine de façon inattendue, COM retourne une erreur à partir du proxy de marshaling pour les appels à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)