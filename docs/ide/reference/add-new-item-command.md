---
title: "Ajouter un nouvel &#233;l&#233;ment, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addnewitem"
helpviewer_keywords: 
  - "Ajouter un nouvel élément (commande)"
  - "File.AddNewItem (commande)"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Ajouter un nouvel &#233;l&#233;ment, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ajoute un nouvel élément de solution \(tel qu'un fichier .htm, .css ou .txt ou un jeu de frames\) à la solution en cours, puis ouvre ce fichier.  
  
## Syntaxe  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## Arguments  
 `filename`  
 Facultatif.  Chemin d'accès et nom de fichier de l'élément à ajouter à la solution en cours.  
  
## Commutateurs  
 \/t:`templatename`  
 Facultatif.  Spécifie le type du fichier à créer.  Si aucun nom de modèle n'est indiqué, un fichier texte est créé par défaut.  
  
 La syntaxe de l'argument \/t:`templatename` reflète les informations affichées dans la boîte de dialogue **Ajouter un nouvel élément de solution**.  Vous devez entrer la catégorie complète suivie du type de fichier, en séparant ces deux informations par une barre oblique inverse \(`\`\) et en entourant la chaîne entière de guillemets doubles.  
  
 Par exemple, pour créer un fichier texte, vous entrez l'argument \/t:`templatename` de la façon suivante.  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e:`editorname`  
 Facultatif.  Nom de l'éditeur dans lequel le fichier doit être ouvert.  Si vous spécifiez l'argument sans fournir de nom d'éditeur, la boîte de dialogue **Ouvrir avec** s'affiche.  
  
 La syntaxe de l'argument \/e:`editorname` utilise les noms d'éditeur tels qu'ils sont affichés dans la boîte de dialogue **Ouvrir avec**, c'est\-à\-dire entre guillemets.  
  
 Par exemple, pour ouvrir une feuille de style dans l'éditeur de code source, vous entrez l'argument \/e:`editorname` de la façon suivante.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Exemple  
 Cet exemple ajoute le nouvel élément de solution MyHTMLpg à la solution en cours.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)