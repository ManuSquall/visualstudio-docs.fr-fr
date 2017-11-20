---
title: IActiveScriptSite::OnScriptTerminate | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informe l’hôte que le script a terminé son exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvarResult`  
 [in] Adresse d’une variable qui contient le résultat de script, ou `NULL` si le script a produit aucun résultat.  
  
 `pexcepinfo`  
 [in] Adresse d’une `EXCEPINFO` structure qui contient des informations sur les exceptions générées lorsque le script terminé, ou `NULL` si aucune exception n’a été générée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Remarques  
 Le moteur de script appelle cette méthode avant l’appel à la [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) méthode, avec l’indicateur SCRIPTSTATE_INITIALIZED, est terminée. Cette méthode peut être utilisée pour retourner l’état d’achèvement et les résultats à l’hôte. Notez que nombreux langages de script, qui sont basés sur la réception des événements de l’ordinateur hôte, les intervalles de durée de vie qui sont définis par l’hôte. Dans ce cas, cette méthode ne peut jamais être appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)