---
title: 'IActiveScript :: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575777"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Fait en sorte que le moteur de script abandonne tout script actuellement chargé, perd son état et libère tous les pointeurs d’interface qu’il possède vers d’autres objets, ce qui permet d’entrer dans un état fermé. Les récepteurs d’événements, le texte du script exécuté immédiatement et les appels de macros qui sont déjà en cours sont terminés avant le changement d’État (utilisez [IActiveScript :: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) pour annuler un thread de script en cours d’exécution). Cette méthode doit être appelée par l’hôte de création avant que l’interface ne soit libérée afin d’éviter les problèmes de référence circulaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|valeur|Signification|  
|-----------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script était déjà à l’état fermé).|  
|`OLESCRIPT_S_PENDING`|La méthode a été mise en file d’attente avec succès, mais l’État n’a pas encore changé. Lorsque l’état change, le site doit être rappelé sur la méthode [IActiveScriptSite :: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|La méthode a réussi, mais le script a déjà été fermé.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)