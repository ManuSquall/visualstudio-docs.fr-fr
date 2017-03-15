---
title: "Ajouter un &#233;l&#233;ment existant, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addexistingitem"
helpviewer_keywords: 
  - "Ajouter un élément existant (commande)"
  - "File.AddExistingItem (commande)"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Ajouter un &#233;l&#233;ment existant, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ajoute un fichier existant à la solution en cours, puis ouvre ce fichier.  
  
## Syntaxe  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## Arguments  
 `filename`  
 Obligatoire.  Chemin d'accès complet et nom du fichier, avec l'extension, de l'élément à ajouter à la solution en cours.  Si le chemin d'accès ou le nom comporte des espaces, tout le chemin d'accès doit être entouré de guillemets doubles.  
  
## Commutateurs  
 \/e:`editorname`  
 Facultatif.  Nom de l'éditeur dans lequel le fichier doit être ouvert.  Si vous spécifiez l'argument sans fournir de nom d'éditeur, la boîte de dialogue **Ouvrir avec** s'affiche.  
  
 La syntaxe de l'argument \/e:`editorname` utilise les noms d'éditeur tels qu'ils sont affichés dans la boîte de dialogue **Ouvrir avec**, c'est\-à\-dire entre guillemets.  Par exemple, pour ouvrir une feuille de style dans l'éditeur de code source, vous entrez l'argument \/e:`editorname` de la façon suivante.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Notes  
 La fonctionnalité de saisie semi\-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.  
  
## Exemple  
 Cet exemple ajoute le fichier Form1.frm à la solution en cours.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)