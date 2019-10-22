---
title: 'IActiveScriptErrorDebug :: GetStackFrame | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptErrorDebug.GetStackFrame
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptErrorDebug::GetStackFrame
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8542f83f926ba1a993527baecd6d5b667671b041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576322"
---
# <a name="iactivescripterrordebuggetstackframe"></a>IActiveScriptErrorDebug::GetStackFrame
Fournit le frame de pile qui est en vigueur pour les erreurs d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppdsf`  
 à Frame de pile pour l’erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode fournit le frame de pile qui est en vigueur pour les erreurs d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)