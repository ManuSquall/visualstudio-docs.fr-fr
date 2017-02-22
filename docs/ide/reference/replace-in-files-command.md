---
title: "Remplacer dans les fichiers, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles (commande)"
  - "Remplacer dans les fichiers (commande)"
  - "ReplaceInFiles (commande)"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Remplacer dans les fichiers, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Remplace le texte dans les fichiers à l'aide d'un sous\-ensemble des options proposées sous l'onglet **Remplacer dans les fichiers** de la fenêtre **Rechercher et remplacer**.  
  
## Syntaxe  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
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
  
 \/ext: `extensions`  
 Facultatif.  Spécifie les extensions des fichiers dans lesquels effectuer la recherche.  
  
 \/keep ou \/k  
 Facultatif.  Spécifie que tous les fichiers modifiés restent ouverts.  
  
 \/lookin: `searchpath`  
 Facultatif.  Répertoire sur lequel porte la recherche.  Si le chemin d'accès comporte des espaces, entourez\-le de guillemets doubles.  
  
 \/options ou \/t  
 Facultatif.  Affiche une liste des paramètres en cours des options de recherche sans effectuer de recherche.  
  
 \/regex ou \/r  
 Facultatif.  Des caractères spéciaux prédéfinis sont utilisés dans l'argument `findwhat` comme notations représentant des modèles de texte plutôt que des caractères littéraux.  Pour une liste exhaustive des caractères d'expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset ou \/e  
 Facultatif.  Rétablit les paramètres par défaut des options de recherche et n'effectue pas de recherche.  
  
 \/stop  
 Facultatif.  Interrompt la recherche en cours, le cas échéant.  Lorsque l'argument `/stop`  a été spécifié, l'opération de remplacement ignore tous les autres arguments.  Par exemple, pour arrêter le remplacement en cours, vous devez taper la syntaxe suivante :  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub ou \/s  
 Facultatif.  Recherche le texte dans les sous\-répertoires du répertoire spécifié à l'aide de l'argument \/lookin:`searchpath`.  
  
 \/text2 ou \/2  
 Facultatif.  Affiche les résultats du remplacement dans la fenêtre **Résultats de la recherche 2**.  
  
 \/wild ou \/l  
 Facultatif.  Des caractères spéciaux prédéfinis sont utilisés dans l'argument `findwhat` comme notations représentant un caractère ou une série de caractères.  
  
 \/word ou \/w  
 Facultatif.  Recherche uniquement les mots entiers.  
  
## Exemple  
 Cet exemple recherche le texte `btnCancel` et le remplace par le texte `btnReset` dans tous les fichiers .cls du répertoire « My Visual Studio Projects » ; il affiche ensuite les résultats du remplacement dans la fenêtre **Résultats de la recherche 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## Voir aussi  
 [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)   
 [Remplacer dans les fichiers](../../ide/replace-in-files.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)