---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs
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
ms.openlocfilehash: 6e17c5abcb21bfaad6de948c3676d29232da66cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944313"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Permet la création d’objets dans le processus d’application par le code qui est out-of-process à l’application.  
  
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
 [in] Identificateur (CLSID) de l’objet à créer de classe.  
  
 `pUnkOuter`  
 [in] Si `NULL`, l’objet n’est pas créé en tant que partie d’un agrégat. Sinon, `pUnkOuter` est un pointeur vers l’objet d’agrégation `IUnknown` interface (le contrôle `IUnknown`).  
  
 `dwClsContext`  
 [in] Contexte d’exécution du code exécutable. Les valeurs proviennent de l’énumération `CLSCTX`.  
  
 `riid`  
 [in] L’identificateur d’interface utilisé pour communiquer avec l’objet.  
  
 `ppvObject`  
 [out] Adresse de variable pointeur qui reçoit le pointeur d’interface demandé dans `riid`. En cas de renvoi, *`ppvObject` contient le pointeur d’interface demandé. En cas d’échec, \* `ppvObject` contient `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode délègue à `CoCreateInstance`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)