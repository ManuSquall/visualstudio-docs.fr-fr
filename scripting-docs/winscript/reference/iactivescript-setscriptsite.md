---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
Informe le moteur de script du site d'interface d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fourni par l'hôte.  Appelez cette méthode avant toutes les autres méthodes d'interface d' [IActiveScript](../../winscript/reference/iactivescript.md) être utilisées.  
  
## Syntaxe  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### Paramètres  
 `pScriptSite`  
 \[in\]  Adresse du site hôte fourni de script à associer à cette instance du moteur de script.  Le site doit être uniquement assigné à cette instance du moteur de script ; il ne peut pas être partagé avec d'autres moteurs de script.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_FAIL`|Une erreur non spécifié rencontrée ; le moteur de script n'a pas pu effectuer lancer le site.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, un site a déjà été défini\).|  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)