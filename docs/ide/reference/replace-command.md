---
title: "Remplacer, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace (commande)"
  - "Remplacer (commande)"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Remplacer, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Remplace le texte dans les fichiers à l'aide d'un sous\-ensemble des options proposées sous l'onglet **Remplacer dans les fichiers** de la fenêtre **Rechercher et remplacer**.  
  
## Syntaxe  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## Arguments  
 `findwhat`  
 Obligatoire.  Le texte à rechercher.  
  
 `replacewith`  
 Obligatoire.  Le texte de remplacement du texte trouvé.  
  
## Commutateurs  
 \/all ou \/a  
 Facultatif.  Remplace toutes les occurrences du texte recherché par le texte de remplacement.  
  
 \/case ou \/c  
 Facultatif.  Il y a correspondance uniquement si le texte trouvé respecte la casse du texte spécifié avec l'argument `findwhat`.  
  
 \/doc ou \/d  
 Facultatif.  Effectue la recherche uniquement dans le document actif.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/hidden ou \/h  
 Facultatif.  Recherche le texte masqué et réduit, par exemple les métadonnées d'un contrôle DTC, une zone masquée du plan d'un document ou encore une classe ou une méthode réduite.  
  
 \/open ou \/o  
 Facultatif.  Recherche le texte dans tous les documents ouverts comme s'il s'agissait d'un document unique.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/options ou \/t  
 Facultatif.  Affiche une liste des paramètres en cours des options de recherche sans effectuer de recherche.  
  
 \/proc ou \/p  
 Facultatif.  Effectue la recherche uniquement dans la procédure en cours.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/regex ou \/r  
 Facultatif.  Des caractères spéciaux prédéfinis sont utilisés dans l'argument `findwhat` comme notations représentant des modèles de texte plutôt que des caractères littéraux.  Pour une liste exhaustive des caractères d'expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset ou \/e  
 Facultatif.  Rétablit les paramètres par défaut des options de recherche et n'effectue pas de recherche.  
  
 \/sel ou \/s  
 Facultatif.  Effectue la recherche uniquement dans la sélection en cours.  Spécifiez l'une des zones de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 \/up ou \/u  
 Facultatif.  Effectue la recherche vers le début du fichier, à partir de l'emplacement actuel du curseur.  Par défaut, les recherches sont effectuées du curseur vers la fin du fichier.  
  
 \/wild ou \/l  
 Facultatif.  Des caractères spéciaux prédéfinis sont utilisés dans l'argument `findwhat` comme notations représentant un caractère ou une série de caractères.  
  
 \/word ou \/w  
 Facultatif.  Recherche uniquement les mots entiers.  
  
## Exemple  
 Cet exemple remplace le texte `btnSend` par le texte `btnSubmit` dans tous les documents ouverts.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## Voir aussi  
 [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)