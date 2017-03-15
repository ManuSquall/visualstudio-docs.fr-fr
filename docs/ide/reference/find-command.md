---
title: "Rechercher, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.find"
helpviewer_keywords: 
  - "Edit.Find (commande)"
  - "Rechercher (commande)"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Rechercher, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fichiers de recherche à l'aide d'un sous\-ensemble des options disponibles sous l'onglet de **Rechercher dans les fichiers** de la fenêtre de **Rechercher et remplacer** .  
  
## Syntaxe  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## Arguments  
 `findwhat`  
 Obligatoire.  Le texte à rechercher.  
  
## Commutateurs  
 \/case ou \/c  
 Facultatif.  Il y a correspondance uniquement si le texte trouvé respecte la casse du texte spécifié avec l'argument `findwhat`.  
  
 \/doc ou \/d  
 Facultatif.  Effectue la recherche uniquement dans le document actif.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/markall ou \/m  
 Facultatif.  Ajoute un graphique à chaque ligne contenant une correspondance du texte recherché dans le document actif.  
  
 \/open ou \/o  
 Facultatif.  Recherche le texte dans tous les documents ouverts comme s'il s'agissait d'un document unique.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/options ou \/t  
 Facultatif.  Affiche une liste des paramètres en cours des options de recherche sans effectuer de recherche.  
  
 \/proc ou \/p  
 Facultatif.  Effectue la recherche uniquement dans la procédure en cours.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/reset ou \/e  
 Facultatif.  Rétablit les paramètres par défaut des options de recherche et n'effectue pas de recherche.  
  
 \/sel ou \/s  
 Facultatif.  Effectue la recherche uniquement dans la sélection en cours.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/up ou \/u  
 Facultatif.  Effectue la recherche vers le début du fichier, à partir de l'emplacement actuel du curseur.  Par défaut, les recherches sont effectuées du curseur vers la fin du fichier.  
  
 \/regex ou \/r  
 Facultatif.  Des caractères spéciaux prédéfinis sont utilisés dans l'argument `findwhat` comme notations représentant des modèles de texte plutôt que des caractères littéraux.  Pour une liste exhaustive des caractères d'expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/wild ou \/l  
 Facultatif.  Des caractères spéciaux prédéfinis sont utilisés dans l'argument `findwhat` comme notations représentant un caractère ou une série de caractères.  
  
 \/word ou \/w  
 Facultatif.  Recherche uniquement les mots entiers.  
  
## Exemple  
 Cet exemple recherche le mot « somestring » en respectant la casse dans la section de code sélectionnée.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## Voir aussi  
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)