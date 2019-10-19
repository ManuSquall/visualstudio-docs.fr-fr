---
title: 'IRemoteDebugApplication :: CreateInstanceAtApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572311"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Autorise la création d’objets dans le processus d’application par du code qui est hors processus de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rclsid`  
 dans Identificateur de classe (CLSID) de l’objet à créer.  
  
 `pUnkOuter`  
 dans Si `NULL`, l’objet n’est pas créé dans le cadre d’un agrégat. Dans le cas contraire, `pUnkOuter` est un pointeur vers l’interface `IUnknown` de l’objet d’agrégation (le `IUnknown` de contrôle).  
  
 `dwClsContext`  
 dans Contexte d’exécution du code exécutable. Les valeurs sont extraites de l’énumération `CLSCTX`.  
  
 `riid`  
 dans Identificateur d’interface utilisé pour communiquer avec l’objet.  
  
 `ppvObject`  
 à Adresse de la variable pointeur qui reçoit le pointeur d’interface demandé dans `riid`. En cas de retour correct, * `ppvObject` contient le pointeur d’interface demandé. En cas d’échec, \* `ppvObject` contient des `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode délègue à `CoCreateInstance`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)