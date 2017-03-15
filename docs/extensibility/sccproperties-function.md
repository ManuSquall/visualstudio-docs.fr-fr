---
title: "SccProperties (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "SccProperties (fonction)"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccProperties (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction affiche les propriétés du contrôle source pour un fichier ou un projet.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpFileName  
 \[in\] Le nom de chemin d'accès complet du fichier ou du projet.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Les propriétés ont été correctement affichées.|  
|SCC\_I\_RELOADFILE|Le système de contrôle de version a modifié les propriétés du fichier, donc l'IDE doit recharger ce fichier.|  
|SCC\_E\_PROJNOTOPEN|Le projet spécifié n'a pas été ouvert dans le contrôle de code source.|  
|SCC\_E\_NOTAUTHORIZED|L'utilisateur n'est pas autorisé à afficher les propriétés de ce fichier ou le projet.|  
|SCC\_E\_FILENOTCONTROLLED|Le fichier spécifié ou le projet n'est pas sous contrôle de code source.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Une erreur inconnue ou générale s'est produite.|  
  
## Notes  
 Le plug\-in de contrôle de code source affiche les propriétés de sa propre boîte de dialogue.  
  
 Les propriétés sont définies par le plug\-in de contrôle de code source et peuvent différer de plug\-in pour le plug\-in. Si le plug\-in permet aux utilisateurs de modifier les propriétés du contrôle de code source d'un fichier, elle doit retourner `SCC_I_RELOAD` pour signaler l'IDE que ce fichier ou le projet doit être rechargé.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)