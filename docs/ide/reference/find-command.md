---
title: Rechercher, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 288fb294ab712713d6be116f46ca159ea40a6e67
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595642"
---
# <a name="find-command"></a>Rechercher, commande
Recherche des fichiers en utilisant un sous-ensemble des options disponibles sous l’onglet **Rechercher dans les fichiers**  de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Arguments
`findwhat` Obligatoire. Texte à rechercher.

## <a name="switches"></a>Commutateurs
/case ou /c\
Option facultative. Il y a correspondance uniquement si les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

/doc ou /d\
Option facultative. Effectue la recherche uniquement dans le document actif. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/markall ou /m\
Option facultative. Ajoute un graphique à chaque ligne contenant une correspondance du texte recherché dans le document actif.

/open ou /o\
Option facultative. Effectue la recherche dans tous les documents ouverts comme s’il s’agissait d’un document unique. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/options ou /t\
Option facultative. Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

/proc ou /p\
Option facultative. Effectue la recherche uniquement dans la procédure en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/reset ou /e\
Option facultative. Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

/sel ou /s\
Option facultative. Effectue la recherche uniquement dans la sélection en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/up ou /u\
Option facultative. Effectue la recherche à partir de l’emplacement actuel vers le début du fichier. Par défaut, les recherches commencent à l’emplacement actuel dans le fichier et s’effectuent vers la fin du fichier.

/regex ou /r\
Option facultative. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

/wild ou /l\
Option facultative. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

/word ou /w\
Option facultative. Recherche uniquement les mots entiers.

## <a name="example"></a>Exemple
Cet exemple recherche le mot « somestring » en respectant la casse dans la section de code sélectionnée.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Voir aussi

- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio, commandes](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
