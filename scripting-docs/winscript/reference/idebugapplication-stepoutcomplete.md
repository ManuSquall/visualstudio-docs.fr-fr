---
title: 'IDebugApplication :: StepOutComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571039"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Signale au gestionnaire de débogage de processus qu’un moteur de langage en mode à étape unique est sur le le même de retourner à son appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Les moteurs de langage appellent cette méthode en mode à étape unique juste avant de retourner à l’appelant. Le gestionnaire de débogage de processus utilise cette opportunité pour notifier à tous les autres moteurs de script qu’ils doivent s’arrêter à la première occasion. Cette technique est l’implémentation des modes d’étape inter-langages.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)