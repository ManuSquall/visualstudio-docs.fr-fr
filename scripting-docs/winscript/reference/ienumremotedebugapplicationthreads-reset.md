---
title: 'IEnumRemoteDebugApplicationThreads :: Reset | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Reset
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Reset
ms.assetid: a6ad8a01-4cc0-4f9c-9cfe-c7448c753473
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab1f2b4afdcaa9cdb6f506c64b1c7563cd218624
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577779"
---
# <a name="ienumremotedebugapplicationthreadsreset"></a>IEnumRemoteDebugApplicationThreads::Reset
Réinitialise une séquence d’énumération au début.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode réinitialise une séquence d’énumération au début.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)