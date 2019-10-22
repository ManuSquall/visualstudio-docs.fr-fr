---
title: 'IDebugApplication :: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a7fd27ec86485d39ee9f13997c1a2db7175afcde
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570983"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Démarre l’environnement de développement intégré (IDE) du débogueur par défaut et attache une session de débogage à cette application, si aucune n’est déjà attachée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée pour implémenter le débogage juste-à-temps.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)