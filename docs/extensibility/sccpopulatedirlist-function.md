---
title: "SccPopulateDirList (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "SccPopulateDirList (fonction)"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# SccPopulateDirList (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction détermine les répertoires et \(éventuellement\) les fichiers sont stockés dans le contrôle de code source, une liste de répertoires à examiner.  
  
## Syntaxe  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 nDirs  
 \[in\] Nombre de chemins d'accès dans la `lpDirPaths` tableau.  
  
 lpDirPaths  
 \[in\] Tableau des chemins d'accès à examiner.  
  
 pfnPopulate  
 \[in\] Fonction de rappel à appeler pour chaque chemin d'accès de répertoire et \(facultatif\) nom de fichier dans `lpDirPaths` \(voir [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Pour plus d'informations\).  
  
 pvCallerData  
 \[in\] Valeur qui doit être passé à la fonction de rappel inchangé.  
  
 Options  
 \[in\] Une combinaison de valeurs qui contrôlent la façon dont sont traités les répertoires \(consultez la section « Indicateurs PopulateDirList » de [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles\).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|L'opération terminée.|  
|SCC\_E\_UNKNOWNERROR|Une erreur s'est produite.|  
  
## Notes  
 Uniquement les répertoires et \(éventuellement\) des noms de fichiers qui sont réellement dans le référentiel de contrôle de code source sont passés à la fonction de rappel.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codes d'erreur](../extensibility/error-codes.md)