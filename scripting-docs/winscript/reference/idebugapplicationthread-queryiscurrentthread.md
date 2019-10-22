---
title: 'IDebugApplicationThread :: QueryIsCurrentThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 189de2448d808b777a21b9353a7adc9f6e3dde24
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574553"
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Détermine si ce thread est le thread en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi et c’est le thread en cours d’exécution.|  
|`S_FALSE`|Il ne s’agit pas du thread en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode détermine si ce thread est le thread en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)