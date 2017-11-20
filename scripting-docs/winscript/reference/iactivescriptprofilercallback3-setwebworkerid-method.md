---
title: "Iactivescriptprofilercallback3::setwebworkerid, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId, méthode
Informe le profileur sur l’ID de travail à utiliser pour cette session de profilage. Si la fonction n’est pas en cours d’exécution dans le contexte de la page, cette méthode n’est pas appelée. La valeur de `webWorkerId` par incréments de 1 pour chaque processus de travail, en commençant à 1. Les valeurs d’ID ne sont pas destinés à être stable au-delà d’une session et ne correspondent qu’à l’ordre dans lequel les threads de travail ont été créés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `webWorkerId`  
 L’ID de travail web.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.