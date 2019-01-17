---
title: Méthode IActiveScriptProfilerCallback3::SetWebWorkerId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347214"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId, méthode
Informe le profileur sur l’ID de travail à utiliser pour cette session de profilage. Si la fonction n’est pas en cours d’exécution dans le contexte de la page, cette méthode n’est pas appelée. La valeur de `webWorkerId` par incréments de 1 pour chaque processus de travail, en commençant à 1. Les valeurs d’ID ne sont pas destinées à être stable au-delà d’une session et ne correspondent qu’à l’ordre dans lequel les employés ont été créés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `webWorkerId`  
 L’ID de travail web.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.