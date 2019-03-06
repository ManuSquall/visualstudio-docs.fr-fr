---
title: ICanHandleException::CanHandleException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 784463f9e465aac005f5454be28a0043069dcb69
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089997"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Détermine si l’appelant du moteur de script peut gérer une exception spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pExcepInfo`  
 [in] Pointeur vers un `EXCEPINFO` structure contenant les informations qui seront signalées si aucun gestionnaire d’exceptions n’est trouvé.  
  
 `pvar`  
 [in] Une valeur associée à l’exception, telles que la valeur levée par un `throw` instruction. Ce paramètre peut avoir la valeur `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|L’appelant peut gérer l’exception|  
|`E_FAIL`|L’appelant ne peut pas gérer l’exception.|  
  
## <a name="remarks"></a>Notes  
 Si un appel à `IDispatchEx::InvokeEx`, ou une méthode similaire, génère une exception, les vérifications de moteur de script pour un appelant dans la chaîne de l’appelant du script qui prend en charge le `ICanHandleException` de l’interface et indique qu’il peut gérer l’exception. Si aucun appelant ne peut gérer l’exception, le moteur de script s’arrête.  
  
## <a name="see-also"></a>Voir aussi  
 [ICanHandleException (Interface)](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)