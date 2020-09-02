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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657679"
---
# <a name="find-command"></a>Rechercher, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recherche des fichiers en utilisant un sous-ensemble des options disponibles sous l’onglet **Rechercher dans les fichiers ** de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` Obligatoire. Texte à rechercher.

## <a name="switches"></a>Commutateurs
 /case ou /c (facultatif). Il y a correspondance uniquement si les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

 /doc ou /d (facultatif). Effectue la recherche uniquement dans le document actif. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /markall ou /m (facultatif). Ajoute un graphique à chaque ligne contenant une correspondance du texte recherché dans le document actif.

 /open ou /o (facultatif). Effectue la recherche dans tous les documents ouverts comme s’il s’agissait d’un document unique. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /options ou /t (facultatif). Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

 /proc ou /p (facultatif). Effectue la recherche uniquement dans la procédure en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /reset ou /e (facultatif). Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

 /sel ou /s (facultatif). Effectue la recherche uniquement dans la sélection en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /up ou /u (facultatif). Effectue la recherche à partir de l’emplacement actuel vers le début du fichier. Par défaut, les recherches commencent à l’emplacement actuel dans le fichier et s’effectuent vers la fin du fichier.

 /regex ou /r (facultatif). Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

 /wild ou /l (facultatif). Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

 /word ou /w (facultatif). Recherche uniquement les mots entiers.

## <a name="example"></a>Exemple
 Cet exemple recherche le mot « somestring » en respectant la casse dans la section de code sélectionnée.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Voir aussi
 [Fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [Visual Studio commandes](../../ide/reference/visual-studio-commands.md) Visual [Studio alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
