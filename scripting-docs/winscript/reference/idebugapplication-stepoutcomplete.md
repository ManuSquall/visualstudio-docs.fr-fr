---
title: IDebugApplication::StepOutComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1798d347fff11a49b945519fd20c370eca75d590
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089919"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Notifie le Gestionnaire de débogage de processus qu’un moteur de langage en mode de pas à pas est sur le point de retourner à son appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Moteurs de langage appellent cette méthode en mode de pas à pas juste avant de retourner à son appelant. Le Gestionnaire de débogage de processus utilise cette opportunité pour notifier tous les autres moteurs de script qui ils doivent s’arrêter à la première occasion. Cette technique est étape comment interlangage modes sont implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)