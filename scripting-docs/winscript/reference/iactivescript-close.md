---
title: IActiveScript::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 886ab1c4c39cf7c64571862bfd28f2fbd1062694
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348801"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Provoque le moteur de script abandonner n’importe quel script actuellement chargé, son état est perdu et libérer les pointeurs d’interface qu’à d’autres objets, donc dans un état fermé. Récepteurs d’événements, le texte de script exécuté immédiatement et appels de macro qui sont déjà en cours d’exécution sont terminés avant les modifications d’état (utilisez [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) d’annuler un thread de script en cours d’exécution). Cette méthode doit être appelée par l’hôte de création avant de l’interface est libéré pour éviter les problèmes de référence circulaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script était déjà dans l’état fermé).|  
|`OLESCRIPT_S_PENDING`|La méthode a été en file d’attente avec succès, mais l’état n’a pas encore changé. Quand les modifications d’état, le site doit être rappelé sur le [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) (méthode).|  
|`S_FALSE`|La méthode a réussi, mais le script a déjà été fermé.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)