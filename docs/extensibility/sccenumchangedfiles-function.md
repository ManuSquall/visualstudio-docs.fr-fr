---
title: "SccEnumChangedFiles (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "SccEnumChangedFiles (fonction)"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccEnumChangedFiles (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtenez la liste des fichiers locaux, cette fonction détermine quels fichiers sont différents dans les versions correspondantes de la base de données de contrôle de code source.  
  
## Syntaxe  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 cFiles  
 \[in\] Nombre de noms de fichier spécifiés dans le `lpFileNames` tableau. Spécifie également la taille de `plIsFileDifferent` tableau.  
  
 lpFileNames  
 \[in\] Tableau des noms de fichier local à vérifier.  
  
 plIsFileDifferent  
 \[dans, out\] Tableau de valeurs indiquant l'état de la différence de chaque fichier \(tableau doit avoir au moins `cFiles` entrées\). Différente de zéro signifie que le fichier est différent.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Opération réussie.|  
|SCC\_UNSPECIFIEDERROR|Erreur générique.|  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)