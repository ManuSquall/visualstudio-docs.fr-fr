---
title: 'ICanHandleException :: CanHandleException | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575721"
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
 dans Pointeur vers une structure `EXCEPINFO` contenant les informations qui seront signalées si aucun gestionnaire d’exceptions n’est trouvé.  
  
 `pvar`  
 dans Valeur associée à l’exception, telle que la valeur levée par une instruction `throw`. Ce paramètre peut avoir la valeur `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’appelant peut gérer l’exception|  
|`E_FAIL`|L’appelant ne peut pas gérer l’exception.|  
  
## <a name="remarks"></a>Notes  
 Si un appel à `IDispatchEx::InvokeEx`, ou une méthode similaire, provoque une exception, le moteur de script recherche un appelant dans la chaîne d’appelant du script qui prend en charge l’interface `ICanHandleException` et indique qu’il peut gérer l’exception. Si aucun appelant ne peut gérer l’exception, le moteur de script s’arrête.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)