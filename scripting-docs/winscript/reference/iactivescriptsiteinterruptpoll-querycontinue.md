---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725159"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permet à un hôte spécifier qu’un script doit s’arrêter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’appel a réussi et que l’hôte autorise le script continuer à exécuter.|  
|`S_FALSE`|L’appel a réussi et les demandes d’hôte qui le script se termine.|  
  
## <a name="remarks"></a>Remarques  
 Le script hébergé doit s’arrêter, sauf si la valeur de retour de la `QueryContinue` méthode est `S_OK`. La valeur de retour `S_FALSE` indique que l’hôte demande explicitement que le script s’arrête.  
  
 Un hôte multithread peut utiliser le `IActiveScript::InterruptScriptThread` méthode pour mettre fin à un script.  
  
## <a name="see-also"></a>Voir aussi  
 [Iactivescriptsiteinterruptpoll, Interface](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)