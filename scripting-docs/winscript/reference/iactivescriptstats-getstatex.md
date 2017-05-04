---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
Retourne une statistique de script personnalisé.  
  
## Syntaxe  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### Paramètres  
 `guid`  
 \[in\]  Spécifie les informations statistiques à retourner.  La sémantique de la statistique correspond à un GUID particulier est entièrement moteur définie.  
  
 `pluHi`  
 \[out\]  Les bits de grande 32 d'un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 \[out\]  les bits du bas 32 d'un entier non signé 64 bits représentant la statistique.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|  
  
## Notes  
 Cette méthode permet un moteur de script personnalisé aux compléments de retour explicite à un hôte personnalisés.  
  
> [!NOTE]
>  Cette méthode n’est pas implémentée pour l’instant.  
  
## Voir aussi  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats, interface](../../winscript/reference/iactivescriptstats-interface.md)