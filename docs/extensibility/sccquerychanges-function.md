---
title: "SccQueryChanges (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryChanges"
helpviewer_keywords: 
  - "SccQueryChanges (fonction)"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccQueryChanges (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction énumère une liste de fichiers, en fournissant des informations sur la modification du nom de chaque fichier via une fonction de rappel donnée.  
  
## Syntaxe  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### Paramètres  
 pContext  
 \[in\] Le pointeur de contexte plug\-in de contrôle de code source.  
  
 nFiles  
 \[in\] Nombre de fichiers dans `lpFileNames` tableau.  
  
 lpFileNames  
 \[in\] Tableau des noms de fichier pour obtenir des informations.  
  
 pfnCallback  
 \[in\] Fonction de rappel à appeler pour chaque nom de fichier dans la liste \(voir [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Pour plus d'informations\).  
  
 pvCallerData  
 \[in\] Valeur qui sera transmis sans modification à la fonction de rappel.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|La requête est terminée avec succès.|  
|SCC\_E\_PROJNOTOPEN|Le projet n'a pas été ouvert dans le contrôle de code source.|  
|SCC\_E\_ACCESSFAILURE|Impossible d'accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|  
|SCC\_E\_NONSPECIFICERROR|Une erreur non spécifiée ou générale s'est produite.|  
  
## Notes  
 Les modifications demandées sont à l'espace de noms : en particulier, changement de nom, l'ajout et suppression d'un fichier.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codes d'erreur](../extensibility/error-codes.md)