---
title: IActiveScriptSite::OnLeaveScript | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informe l’hôte que le moteur de script a été retournée à partir de l’exécution de code de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="remarks"></a>Remarques  
 Le moteur de script doit appeler cette méthode pour restituer le contrôle à une application appelante qui a entré le moteur de script. Par exemple, si le script appelle un objet qui déclenche un événement géré par le moteur de script, le moteur de script doit appeler le [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) méthode avant l’exécution de l’événement et vous devez appeler `IActiveScriptSite::OnLeaveScript`après l’exécution de l’événement avant de retourner à l’objet qui a déclenché l’événement. Les appels à cette méthode peuvent être imbriqués. Chaque appel à `IActiveScriptSite::OnEnterScript` nécessite un appel correspondant à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)