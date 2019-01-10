---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8ff7c3d531b46fa6681776e79fbb73f6d1efca2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087111"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informe l’hôte que le script a terminé son exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvarResult`  
 [in] Adresse d’une variable qui contient le résultat de script, ou `NULL` si le script a produit aucun résultat.  
  
 `pexcepinfo`  
 [in] Adresse d’un `EXCEPINFO` structure qui contient des informations sur les exceptions générées lorsque le script s’est arrêté, ou `NULL` si aucune exception n’a été générée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script appelle cette méthode avant d’appeler le [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) méthode, avec l’indicateur SCRIPTSTATE_INITIALIZED, est terminée. Cette méthode peut être utilisée pour retourner l’état d’achèvement et les résultats à l’hôte. Notez que plusieurs langages de script, qui sont basés sur la réception des événements à partir de l’hôte, vie étendues qui sont définies par l’hôte. Dans ce cas, cette méthode ne peut jamais être appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)