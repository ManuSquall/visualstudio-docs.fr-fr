---
title: "Enregistrer la sortie de la fen&#234;tre de commande, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "Enregistrer la sortie de la fenêtre Commande (commande)"
  - "View.LogCommandWindowOutput (commande)"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Enregistrer la sortie de la fen&#234;tre de commande, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Copie dans un fichier toutes les entrées et sorties de la fenêtre **Commande**.  
  
## Syntaxe  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## Arguments  
 `filename`  
 Facultatif.  Nom du fichier journal.  Par défaut, le fichier est créé dans le dossier du profil de l'utilisateur.  Si le nom de fichier spécifié existe déjà, le journal est ajouté à la fin du fichier existant.  Si aucun fichier n'est spécifié, le dernier fichier spécifié est utilisé.  Si aucun fichier n'a été spécifié précédemment, le fichier journal cmdline.log est créé par défaut.  
  
> [!TIP]
>  Pour modifier l'emplacement d'enregistrement du fichier journal, entrez le chemin d'accès complet du fichier, en l'entourant de guillemets doubles s'il comporte des espaces.  
  
## Commutateurs  
 \/on  
 Facultatif.  Démarre l'enregistrement du journal, pour la fenêtre **Commande**, dans le fichier spécifié et ajoute les nouvelles informations à la fin de ce fichier.  
  
 \/off  
 Facultatif.  Arrête l'enregistrement du journal pour la fenêtre **Commande**.  
  
 \/overwrite  
 Facultatif.  Si le fichier spécifié dans l'argument `filename` est identique à un fichier existant, celui\-ci est remplacé.  
  
## Notes  
 Si aucun fichier n'est spécifié, le fichier journal cmdline.log est créé par défaut.  L'alias par défaut de cette commande est Log.  
  
## Exemples  
 Cet exemple crée le fichier journal cmdlog, puis démarre l'enregistrement des commandes.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Cet exemple arrête l'enregistrement des commandes.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Cet exemple reprend l'enregistrement des commandes dans le dernier fichier journal utilisé.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)