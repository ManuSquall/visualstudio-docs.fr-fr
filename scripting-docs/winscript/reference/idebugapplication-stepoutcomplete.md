---
title: IDebugApplication::StepOutComplete | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c344f0316bda6ed5ef895c1b88ae7b1a6465e73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Notifie le Gestionnaire de processus de débogage qu’un moteur de langue en mode de pas à pas est sur le point de retourner à son appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Moteurs de langue appellent cette méthode en mode de la seule étape juste avant de retourner à son appelant. Le Gestionnaire de processus de débogage utilise cette opportunité pour informer tous les autres moteurs de script qui ils doivent s’arrêter dès que possible. Cette technique est l’étape comment interlangage modes sont implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)