---
title: Rechercher, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ffa71b12a0cbe72b2c4fae479990e112fc75940
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790312"
---
# <a name="find-command"></a>Rechercher, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Recherche des fichiers en utilisant un sous-ensemble des options disponibles sous l’onglet **Rechercher dans les fichiers**  de la fenêtre **Rechercher et remplacer**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Arguments  
 `findwhat`  
 Obligatoire. Texte à rechercher.  
  
## <a name="switches"></a>Commutateurs  
 /case ou /c  
 Optionnel. Il y a correspondance uniquement si les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.  
  
 /doc ou /d  
 Optionnel. Effectue la recherche uniquement dans le document actif. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 /markall ou /m  
 Optionnel. Ajoute un graphique à chaque ligne contenant une correspondance du texte recherché dans le document actif.  
  
 /open ou /o  
 Optionnel. Effectue la recherche dans tous les documents ouverts comme s’il s’agissait d’un document unique. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 /options ou /t  
 Optionnel. Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.  
  
 /proc ou /p  
 Optionnel. Effectue la recherche uniquement dans la procédure en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 /reset ou /e  
 Optionnel. Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.  
  
 /sel ou /s  
 Optionnel. Effectue la recherche uniquement dans la sélection en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.  
  
 /up ou /u  
 Optionnel. Effectue la recherche à partir de l’emplacement actuel vers le début du fichier. Par défaut, les recherches commencent à l’emplacement actuel dans le fichier et s’effectuent vers la fin du fichier.  
  
 /regex ou /r  
 Optionnel. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /wild ou /l  
 Optionnel. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.  
  
 /word ou /w  
 Optionnel. Recherche uniquement les mots entiers.  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche le mot « somestring » en respectant la casse dans la section de code sélectionnée.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
