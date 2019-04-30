---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
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
ms.openlocfilehash: 63ce45c0973d65d240136d7b42aef0c078b00c9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992292"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permet à un hôte spécifier qu’un script doit s’arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|L’appel a réussi et que l’hôte autorise le script pour continuer à s’exécuter.|  
|`S_FALSE`|L’appel a réussi et les demandes d’hôte qui se terminent le script.|  
  
## <a name="remarks"></a>Notes  
 Le script hébergé doit se terminer, sauf si la valeur de retour de la `QueryContinue` méthode est `S_OK`. La valeur de retour `S_FALSE` indique que l’hôte demande explicitement que le script s’arrête.  
  
 Un hôte multithread peut utiliser le `IActiveScript::InterruptScriptThread` méthode pour mettre fin à un script.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSiteInterruptPoll (Interface)](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)