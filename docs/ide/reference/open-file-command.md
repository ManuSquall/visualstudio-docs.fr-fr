---
title: "Ouvrir un fichier, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile (commande)"
  - "of (commande)"
  - "Ouvrir un fichier (commande)"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Ouvrir un fichier, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre un fichier existant et vous permet de spécifier un éditeur.  
  
## Syntaxe  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## Arguments  
 `filename`  
 Obligatoire.  Chemin d'accès complet ou partiel et nom du fichier à ouvrir.  Les chemins d'accès comportant des espaces doivent être entourés de guillemets doubles.  
  
## Commutateurs  
 \/e:`editorname`  
 Facultatif.  Nom de l'éditeur dans lequel le fichier doit être ouvert.  Si vous spécifiez l'argument sans fournir de nom d'éditeur, la boîte de dialogue **Ouvrir avec** s'affiche.  
  
 \/e : la syntaxe d'argument d'`editorname` utilise les noms d'éditeur tels qu'ils apparaissent dans l'ouvrir avec la boîte de dialogue, entre guillemets.  
  
 Par exemple, pour ouvrir un fichier dans l'éditeur de code source, vous entrez l'argument \/e:`editorname` de la façon suivante.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Notes  
 La fonctionnalité de saisie semi\-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.  
  
## Exemple  
 Cet exemple ouvre la feuille de style "Test1.css" dans l'éditeur de code source.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Fenêtre Exécution](../../ide/reference/immediate-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)