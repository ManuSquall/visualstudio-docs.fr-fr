---
title: IApplicationDebugger::CreateInstanceAtDebugger | Documents Microsoft
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
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725769"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Permet la création d’objets dans le processus du débogueur par le code qui est out-of-process pour le débogueur.  
  
> [!IMPORTANT]
>  Cette méthode ne doit pas être implémentée, car elle permet de créer des objets arbitraires dans un thread de débogueur de confiance de code non fiable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Si `NULL`, l’objet n’est pas créé en tant que partie d’un agrégat. Dans le cas contraire, `pUnkOuter` est un pointeur vers l’objet d’agrégation `IUnknown` interface (le contrôle `IUnknown`).  
  
 `dwClsContext`  
 [in] Contexte d’exécution du code exécutable. Les valeurs sont extraites à partir de l’énumération `CLSCTX`.  
  
 `riid`  
 [in] L’identificateur d’interface utilisé pour communiquer avec l’objet.  
  
 `ppvObject`  
 [out] Adresse de variable pointeur qui reçoit le pointeur d’interface demandé dans `riid`. Lors du retour réussi, *`ppvObject` contient le pointeur d’interface demandé. En cas d’échec, \* `ppvObject` contient `NULL`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode délègue à `CoCreateInstance`.  
  
 La méthode n’est pas implémentée actuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)