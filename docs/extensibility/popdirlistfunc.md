---
title: "POPDIRLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "Fonction de rappel POPDIRLISTFUNC"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il s'agit d'une fonction de rappel à le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) \(fonction\) pour mettre à jour un ensemble de répertoires et \(éventuellement\) des noms de fichiers qui sont sous contrôle de code source.  
  
 Le `POPDIRLISTFUNC` rappel doit être appelé uniquement pour les répertoires et les noms de fichiers \(dans la liste donnée à le `SccPopulateDirList` fonction\) qui sont réellement sous contrôle de code source.  
  
## Signature  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## Paramètres  
 pvCallerData  
 \[in\] Valeur de l'utilisateur à [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bOptions  
 \[in\] `TRUE` Si le nom de `lpDirectoryOrFileName` est un répertoire ; sinon, le nom est un nom de fichier.  
  
 lpDirectoryOrFileName  
 \[in\] Chemin d'accès local complet à un nom de répertoire ou un fichier qui est sous contrôle de code source.  
  
## Valeur de retour  
 L'IDE retourne un code d'erreur approprié :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Continuer le traitement.|  
|SCC\_I\_OPERATIONCANCELED|Arrêter le traitement.|  
|SCC\_E\_xxx|Une erreur de contrôle de source appropriée doit arrêter le traitement.|  
  
## Notes  
 Si le `fOptions` paramètre de la `SccPopulateDirList` fonction contient le `SCC_PDL_INCLUDEFILES` indicateur, la liste contient éventuellement les noms de fichiers ainsi que les noms de répertoire.  
  
## Voir aussi  
 [Fonctions de rappel implémentées par l'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codes d'erreur](../extensibility/error-codes.md)