---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
Retourne la position de départ et la longueur d'une entrée.  
  
## Syntaxe  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### Paramètres  
 `pichMin`  
 \[out\]  Pour les objets d' `IScriptEntry` qui spécifient un bloc de script, retourne 0.  
  
 Pour les objets d' `IScriptEntry` qui spécifient un objet de fonction, retourne la position de départ de la fonction dans le bloc de script en cours.  
  
 Pour les objets d' `IScriptScriptlet` , retourne 0.  
  
 `pcch`  
 \[out\]  Pour les objets d' `IScriptEntry` qui spécifient un bloc de script, retourne la longueur du texte.  
  
 Pour les objets d' `IScriptEntry` qui spécifient un objet de fonction, retourne la longueur de la définition de fonction.  
  
 Pour les objets d' `IScriptScriptlet` , retourne la longueur de l'entrée.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)