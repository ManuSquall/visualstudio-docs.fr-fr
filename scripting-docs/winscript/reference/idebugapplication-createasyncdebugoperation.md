---
title: 'IDebugApplication :: CreateAsyncDebugOperation | Microsoft Docs'
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
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575560"
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
 dans Objet de l’opération de débogage synchrone.  
  
 `ppado`  
 à Objet de l’opération de débogage asynchrone.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet aux moteurs de langage d’évaluer les expressions de manière asynchrone sans synchronisation explicite avec le thread du débogueur. Pour plus d’informations, consultez [interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) et [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 @No__t_1 de l' [interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)  
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)