---
title: IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 30051276b682bdf906db72bc2682e1c5d58c455a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090699"
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