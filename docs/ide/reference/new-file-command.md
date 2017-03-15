---
title: "Nouveau fichier, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile (commande)"
  - "Nouveau fichier (commande)"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Nouveau fichier, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crée un fichier et l'ouvre.  Le fichier est enregistré dans le dossier Fichiers divers.  
  
## Syntaxe  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## Arguments  
 `filename`  
 Facultatif.  Nom du fichier.  Si aucun nom n'est spécifié, un nom par défaut est utilisé.  Si aucun nom de modèle n'est indiqué, un fichier texte est créé par défaut.  
  
## Commutateurs  
 \/t:`templatename`  
 Facultatif.  Spécifie le type du fichier à créer.  
  
 \/t : la syntaxe d'argument d'`templatename` reflète les informations contenues dans la boîte de dialogue Fichier.  Entrez le nom de la catégorie suivi d'une barre oblique inverse \(`\`\) et du nom du modèle, et mettez la chaîne entre guillemets.  
  
 Par exemple, pour créer un fichier source [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)], entrez l'argument \/t:`templatename` de la façon suivante.  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 L'exemple ci\-dessus indique que le modèle de fichier C\+\+ fait partie de la catégorie Visual C\+\+ dans la boîte de dialogue **Nouveau fichier**.  
  
 \/e:`editorname`  
 Facultatif.  Nom de l'éditeur dans lequel le fichier doit être ouvert.  Si vous spécifiez l'argument sans fournir de nom d'éditeur, la boîte de dialogue **Ouvrir avec** s'affiche.  
  
 \/e : la syntaxe d'argument d'`editorname` utilise les noms d'éditeur tels qu'ils apparaissent dans l'ouvrir avec la boîte de dialogue, entre guillemets.  
  
 Par exemple, pour ouvrir un fichier dans l'éditeur de code source, vous entrez l'argument \/e:`editorname` de la façon suivante.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Exemple  
 Cet exemple crée une nouvelle page Web, appelée test1.htm, puis l'ouvre dans l'éditeur de code source.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Fenêtre Exécution](../../ide/reference/immediate-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)