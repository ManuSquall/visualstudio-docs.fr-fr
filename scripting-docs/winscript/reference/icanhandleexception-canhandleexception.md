---
title: ICanHandleException::CanHandleException | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Détermine si l’appelant du moteur de script peut gérer une exception spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pExcepInfo`  
 [in] Pointeur vers un `EXCEPINFO` structure contenant les informations qui seront signalées si aucun gestionnaire d’exceptions n’est trouvé.  
  
 `pvar`  
 [in] Une valeur associée à l’exception, telles que la valeur renvoyée par un `throw` instruction. Ce paramètre peut avoir la valeur `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’appelant peut gérer l’exception|  
|`E_FAIL`|L’appelant ne peut pas gérer l’exception.|  
  
## <a name="remarks"></a>Remarques  
 Si un appel à `IDispatchEx::InvokeEx`, ou une méthode similaire, provoque une exception, le moteur de script vérifie pour un appelant dans la chaîne de l’appelant du script qui prend en charge la `ICanHandleException` de l’interface et indique qu’il peut traiter l’exception. Si aucun appelant ne peut gérer l’exception, le moteur de script s’arrête.  
  
## <a name="see-also"></a>Voir aussi  
 [ICanHandleException (Interface)](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)