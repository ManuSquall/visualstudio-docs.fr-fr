---
title: 'IActiveScriptSiteInterruptPoll :: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572240"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permet à un hôte de spécifier qu’un script doit se terminer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’appel a réussi et l’hôte autorise l’exécution du script.|  
|`S_FALSE`|L’appel a réussi et l’hôte demande que le script se termine.|  
  
## <a name="remarks"></a>Notes  
 Le script hébergé doit se terminer, sauf si la valeur de retour de la méthode `QueryContinue` est `S_OK`. Une valeur de retour de `S_FALSE` indique que l’hôte demande explicitement que le script se termine.  
  
 Un hôte multithread peut utiliser la méthode `IActiveScript::InterruptScriptThread` pour mettre fin à un script.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)