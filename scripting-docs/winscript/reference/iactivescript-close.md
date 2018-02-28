---
title: IActiveScript::Close | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Force le moteur de script à n’importe quel script actuellement chargé d’abandon, son état est perdu et libérer les pointeurs d’interface qu’à d’autres objets, donc dans un état fermé. Récepteurs d’événements, le texte du script exécuté immédiatement et appels de macro qui sont déjà en cours d’exécution sont terminés avant les modifications d’état (utilisez [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) d’annuler un thread en cours d’exécution de script). Cette méthode doit être appelée par l’hôte de création avant de l’interface est libérée pour éviter les problèmes de référence circulaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script était déjà dans l’état fermé).|  
|`OLESCRIPT_S_PENDING`|La méthode a été en file d’attente avec succès, mais l’état n’a pas encore changé. Lorsque les modifications d’état, le site est rappelé sur le [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) (méthode).|  
|`S_FALSE`|La méthode a réussi, mais le script a déjà été fermé.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)