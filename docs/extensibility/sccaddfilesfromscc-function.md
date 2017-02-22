---
title: "SccAddFilesFromSCC (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "SccAddFilesFromSCC (fonction)"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFilesFromSCC (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction ajoute une liste de fichiers à partir du contrôle de code source pour le projet actuellement ouvert.  
  
## Syntaxe  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpUser  
 \[dans, out\] Le nom d'utilisateur \(jusqu'à SCC\_USER\_SIZE, y compris le terminateur null\).  
  
 lpAuxProjPath  
 \[dans, out\] Chaîne auxiliaire qui identifie le projet \(jusqu'à `SCC_PRJPATH_`taille, y compris le terminateur null\).  
  
 cFiles  
 \[in\] Nombre de fichiers donné par `lpFilePaths`.  
  
 lpFilePaths  
 \[dans, out\] Tableau des noms de fichier à ajouter au projet actuel.  
  
 lpDestination  
 \[in\] Le chemin de destination où les fichiers doivent être écrites.  
  
 lpComment  
 \[in\] Le commentaire à appliquer à chacun des fichiers à ajouter.  
  
 pbResults  
 \[dans, out\] Tableau d'indicateurs ensemble pour indiquer la réussite \(différente de zéro ou TRUE\) ou échec \(zéro ou FALSE\) pour chaque fichier \(taille du tableau doit être au moins `cFiles` long\).  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_E\_PROJNOTOPEN|Projet n'est pas ouvert.|  
|SCC\_E\_OPNOTPERFORMED|Connexion n'est pas le même projet, tel que spécifié par `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|Utilisateur n'est pas autorisé à mettre à jour la base de données.|  
|SCC\_E\_NONSPECIFICERROR|Erreur inconnue.|  
|SCC\_I\_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)