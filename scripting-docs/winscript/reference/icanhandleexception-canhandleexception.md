---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
Détermine si l'appel du moteur de script peut gérer une exception spécifiée.  
  
## Syntaxe  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### Paramètres  
 `pExcepInfo`  
 \[in\]  Pointeur vers une structure d' `EXCEPINFO` contenant les informations qui seront enregistrées si aucun gestionnaire d'exceptions n'est trouvé.  
  
 `pvar`  
 \[in\]  Une valeur est associé à l'exception, telle que la valeur renvoyée par une instruction d' `throw` .  Ce paramètre peut être `NULL`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|l'appelant peut gérer l'exception|  
|`E_FAIL`|l'appelant ne peut pas gérer l'exception.|  
  
## Notes  
 Si un appel à `IDispatchEx::InvokeEx`, ou une méthode semblable, provoque une exception, le moteur de script vérifie un appelant dans la chaîne de l'appel du script qui prend en charge l'interface d' `ICanHandleException` et indique qu'il peut gérer l'exception.  Si aucun appelant ne peut gérer l'exception, le moteur de script s'arrête.  
  
## Voir aussi  
 [ICanHandleException, interface](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)