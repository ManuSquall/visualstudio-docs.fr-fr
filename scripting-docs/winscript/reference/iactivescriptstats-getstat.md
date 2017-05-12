---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
Retourne un des statistiques standard de script.  
  
## Syntaxe  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### Paramètres  
 `stid`  
 \[in\]  Spécifie les informations statistiques à retourner.  Doit avoir la valeur :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|Retourne le nombre d'instructions exécutées comme le script démarré ou les statistiques ont été réinitialisé.|  
  
 `pluHi`  
 \[out\]  Les bits de grande 32 d'un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 \[out\]  les bits du bas 32 d'un entier non signé 64 bits représentant la statistique.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées aux valeurs dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne une des statistiques standard de script.  
  
## Voir aussi  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats, interface](../../winscript/reference/iactivescriptstats-interface.md)