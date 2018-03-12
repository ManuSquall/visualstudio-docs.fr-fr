---
title: IActiveScriptSite::OnEnterScript | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informe l’hôte que le moteur de script a commencé l’exécution du code de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Remarques  
 Le moteur de script doit appeler cette méthode sur chaque entrée ou sur une nouvelle entrée dans le moteur de script. Par exemple, si le script appelle un objet qui déclenche un événement géré par le moteur de script, le moteur de script doit appeler `IActiveScriptSite::OnEnterScript` avant l’exécution de l’événement et doit appeler le [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) méthode après exécution de l’événement, mais avant de retourner à l’objet qui a déclenché l’événement. Les appels à cette méthode peuvent être imbriqués. Chaque appel à cette méthode nécessite un appel correspondant à `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)