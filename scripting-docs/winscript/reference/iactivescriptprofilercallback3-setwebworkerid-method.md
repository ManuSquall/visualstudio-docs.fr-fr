---
title: "IActiveScriptProfilerCallback3::SetWebWorkerId, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerCallback3::SetWebWorkerId, m&#233;thode
Informe le profileur sur l'ID de travail de l'utiliser pour cette session de profilage.  Si la fonction ne s'exécute pas dans le contexte de la page, cette méthode n'est pas appelée.  La valeur d' `webWorkerId` incrémente par 1 pour chaque ouvrier, en commençant par 1.  Les valeurs d'ID ne sont pas destinées à être stable au delà d'une session, et correspondent uniquement à l'ordre dans lequel les ouvriers ont été créés.  
  
## Syntaxe  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### Paramètres  
 `webWorkerId`  
 L'ID d'ouvrier de site Web  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.