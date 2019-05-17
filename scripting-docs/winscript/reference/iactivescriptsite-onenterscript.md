---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5505b30bbfd4e1cbc33022d38d7b7170ffd37dd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992691"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informe l’hôte que le moteur de script a commencé l’exécution du code de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script doit appeler cette méthode sur chaque entrée ou sur une nouvelle entrée dans le moteur de script. Par exemple, si le script appelle un objet qui déclenche un événement géré par le moteur de script, le moteur de script doit appeler `IActiveScriptSite::OnEnterScript` avant l’exécution de l’événement et doit appeler le [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) méthode après l’exécution de l’événement, mais avant de retourner à l’objet qui a déclenché l’événement. Appels à cette méthode peuvent être imbriquées. Chaque appel à cette méthode nécessite un appel correspondant à `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)