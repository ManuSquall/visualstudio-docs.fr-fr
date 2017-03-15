---
title: "Afficher la source, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource (commande)"
  - "Afficher la source (commande)"
  - "ListSource (commande)"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Afficher la source, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche les lignes spécifiées du code source.  
  
## Syntaxe  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## Commutateurs  
 \/Count:`number`  
 Facultatif.  Spécifie le nombre de lignes à afficher.  
  
 \/Current  
 Facultatif.  Affiche la ligne en cours.  
  
 \/File:`filename`  
 Facultatif.  Chemin d'accès du fichier à afficher.  Si aucun nom de fichier n'est spécifié, la commande affiche le code source de la ligne de l'instruction actuelle.  
  
 \/Line:`number`  
 Facultatif.  Affiche un numéro de ligne spécifique.  
  
 \/ShowLineNumbers:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les numéros de ligne.  
  
## Notes  
  
## Exemple  
 Cet exemple répertorie le code source de ligne 4 du fichier Form1.vb, en affichant les numéros de ligne.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)