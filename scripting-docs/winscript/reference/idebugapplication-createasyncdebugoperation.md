---
title: IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c60c84dbd3be9248e2bd075e65d53f7f9361d0b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991015"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Fournit un accès asynchrone à une opération de débogage synchrone donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psdo`  
 [in] L’objet d’opération de débogage synchrone.  
  
 `ppado`  
 [out] L’objet d’opération de débogage asynchrone.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet de moteurs de langage évaluer les expressions de façon asynchrone sans synchronisation explicitement avec le thread de débogueur. Pour plus d’informations, consultez [IDebugSyncOperation (Interface)](../../winscript/reference/idebugsyncoperation-interface.md) et [IDebugAsyncOperation (Interface)](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation (Interface)](../../winscript/reference/idebugsyncoperation-interface.md)   
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)