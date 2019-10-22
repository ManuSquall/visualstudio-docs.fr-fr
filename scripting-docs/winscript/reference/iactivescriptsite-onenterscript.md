---
title: 'IActiveScriptSite :: OnEnterScript | Microsoft Docs'
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
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570366"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informe l’hôte que le moteur de script a commencé à exécuter le code de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script doit appeler cette méthode à chaque entrée ou réentrée dans le moteur de script. Par exemple, si le script appelle un objet qui déclenche ensuite un événement géré par le moteur de script, le moteur de script doit appeler `IActiveScriptSite::OnEnterScript` avant d’exécuter l’événement, et doit appeler la méthode [IActiveScriptSite :: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) après l’exécution de l’événement. mais avant de retourner à l’objet qui a déclenché l’événement. Les appels à cette méthode peuvent être imbriqués. Chaque appel à cette méthode requiert un appel correspondant à `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)