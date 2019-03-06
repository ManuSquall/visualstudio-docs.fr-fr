---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6af315f25aa333ace4be7bb8e3584573f0cfd1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090920"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Permet la création d’objets dans le processus du débogueur par le code qui est out-of-process au débogueur.  
  
> [!IMPORTANT]
>  Cette méthode ne doit pas être implémentée, car elle permet de créer des objets arbitraires dans un thread de débogueur de confiance de code non fiable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
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
  
 La méthode n’est pas implémentée actuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)