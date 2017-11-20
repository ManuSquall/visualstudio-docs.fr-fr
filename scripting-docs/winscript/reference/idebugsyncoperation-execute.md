---
title: IDebugSyncOperation::Execute | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69e07c646bfa176f5e2dc07539f301a8ef5c5273
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Mode synchrone effectue l’opération et retourne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunkResult`  
 [out] Le paramètre de l’objet retourné par l’opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_ABORT`|L’opération a été abandonnée en appelant le `IDebugSyncOperation::InProgressAbort` (méthode).|  
  
## <a name="remarks"></a>Remarques  
 Le Gestionnaire de déboguer des processus dans le thread cible appelle la `Execute` méthode synchrone.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)