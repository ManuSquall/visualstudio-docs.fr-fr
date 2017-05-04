---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CreateInstanceAtApplication"
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::CreateInstanceAtApplication
Permet la création des objets dans les processus d'application par le code qui est hors processus à l'application.  
  
## Syntaxe  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### Paramètres  
 `rclsid`  
 \[in\]  Identificateur de classe \(CLSID\) de l'objet à créer.  
  
 `pUnkOuter`  
 \[in\]  Si `NULL`, l'objet n'est pas créé dans le cadre d'un agrégat.  Sinon, `pUnkOuter` est un pointeur vers l'interface d' `IUnknown` de l'objet global \( `IUnknown`de contrôle\).  
  
 `dwClsContext`  
 \[in\]  Contexte du code exécutable en cours de exécution.  Les valeurs sont prises de l'énumération `CLSCTX`.  
  
 `riid`  
 \[in\]  L'identificateur d'interface utilisé pour communiquer avec l'objet.  
  
 `ppvObject`  
 \[out\] Adresse de la variable du pointeur qui reçoit le pointeur d'interface demandé dans `riid`.  Lors de le retour de réussite, \*`ppvObject` contient le pointeur d'interface demandé.  En cas de échec, \*`ppvObject` contient `NULL`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Délégués de cette méthode à `CoCreateInstance`.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)