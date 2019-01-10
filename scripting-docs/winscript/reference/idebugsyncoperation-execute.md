---
title: IDebugSyncOperation::Execute | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8c10973bddef45321b9942afef05a696010433f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090218"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Mode synchrone effectue l’opération et retourne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppunkResult`  
 [out] Le paramètre d’objet retourné par l’opération.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_ABORT`|L’opération a été abandonnée en appelant le `IDebugSyncOperation::InProgressAbort` (méthode).|  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire de débogage de processus dans le thread cible appelle le `Execute` méthode synchrone.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)