---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
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
ms.openlocfilehash: da39058a8f069c4799835108372d11849d86444e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160743"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informe l’hôte que le moteur de script a retourné de l’exécution de code de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Notes  
 Le moteur de script doit appeler cette méthode pour restituer le contrôle à une application appelante qui a entré le moteur de script. Par exemple, si le script appelle un objet qui déclenche un événement géré par le moteur de script, le moteur de script doit appeler le [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) méthode avant d’exécuter l’événement et vous devez appeler `IActiveScriptSite::OnLeaveScript`après l’exécution de l’événement avant de retourner à l’objet qui a déclenché l’événement. Appels à cette méthode peuvent être imbriquées. Chaque appel à `IActiveScriptSite::OnEnterScript` nécessite un appel correspondant à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)