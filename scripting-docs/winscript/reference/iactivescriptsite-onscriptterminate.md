---
title: 'IActiveScriptSite :: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570201"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informe l’hôte que l’exécution du script est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvarResult`  
 dans Adresse d’une variable qui contient le résultat du script, ou `NULL` si le script n’a produit aucun résultat.  
  
 `pexcepinfo`  
 dans Adresse d’une structure `EXCEPINFO` qui contient des informations sur les exceptions générées lorsque le script s’est terminé, ou `NULL` si aucune exception n’a été générée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script appelle cette méthode avant l’appel à la méthode [IActiveScriptSite :: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , avec l’indicateur SCRIPTSTATE_INITIALIZED défini, est terminé. Cette méthode peut être utilisée pour retourner l’état d’achèvement et les résultats à l’hôte. Notez que de nombreux langages de script, basés sur la réception d’événements à partir de l’hôte, ont des étendues de durée de vie définies par l’hôte. Dans ce cas, cette méthode ne peut jamais être appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)