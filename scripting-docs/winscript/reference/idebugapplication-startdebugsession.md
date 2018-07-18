---
title: IDebugApplication::StartDebugSession | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StartDebugSession
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aea5caead4921206428c2f1f36b74d057c8cef36
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725439"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Démarre l’environnement de développement intégré de débogueur par défaut (IDE) et l’attache une session de débogage de cette application, si un n’est pas déjà attaché.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est utilisée pour implémenter le débogage juste-à-temps.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)