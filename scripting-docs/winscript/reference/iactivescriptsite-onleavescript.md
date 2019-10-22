---
title: 'IActiveScriptSite :: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570317"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informe l’hôte que le moteur de script a retourné à partir de l’exécution du code de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script doit appeler cette méthode avant de restituer le contrôle à une application appelante qui a entré le moteur de script. Par exemple, si le script appelle un objet qui déclenche ensuite un événement géré par le moteur de script, le moteur de script doit appeler la méthode [IActiveScriptSite :: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) avant d’exécuter l’événement et doit appeler `IActiveScriptSite::OnLeaveScript` après l’exécution de l’événement. avant de retourner à l’objet qui a déclenché l’événement. Les appels à cette méthode peuvent être imbriqués. Chaque appel à `IActiveScriptSite::OnEnterScript` nécessite un appel correspondant à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)