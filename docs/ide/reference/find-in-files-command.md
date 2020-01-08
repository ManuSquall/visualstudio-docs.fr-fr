---
title: Rechercher dans les fichiers, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d313c29be1d5fb4f1be1febe9b5b7cd32e7e11
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569580"
---
# <a name="find-in-files-command"></a>Rechercher dans les fichiers, commande
Recherche des fichiers en utilisant un sous-ensemble des options disponibles sous l’onglet **Rechercher dans les fichiers**  de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments

`findwhat`\
Requis. Texte à rechercher.

## <a name="switches"></a>Commutateurs
/case ou /c\
Option facultative. Il y a correspondance uniquement si les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

/ext: `extensions`\
Option facultative. Spécifie les extensions des fichiers dans lesquels effectuer la recherche. Si aucune extension n’est spécifiée, l’extension précédemment spécifiée est utilisée (le cas échéant).

/lookin: `searchpath`\
Option facultative. Répertoire dans lequel effectuer une recherche. Si le chemin contient des espaces, placez le chemin complet entre guillemets.

/names ou /n\
Option facultative. Affiche la liste des fichiers qui contiennent des correspondances.

/options ou /t\
Option facultative. Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

/regex ou /r\
Option facultative. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

/reset ou /e\
Option facultative. Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

/stop\
Option facultative. Arrête l’opération de recherche en cours, le cas échant. La recherche ignore tous les autres arguments si `/stop` est spécifié. Par exemple, pour arrêter la recherche en cours, entrez ce qui suit :

```cmd
>Edit.FindinFiles /stop
```

/sub ou /s\
Option facultative. Recherche dans les sous-dossiers du répertoire qui est spécifié dans l’argument /lookin:`searchpath`.

/text2 ou /2\
Option facultative. Affiche les résultats de la recherche dans la fenêtre Résultats de la recherche 2.

/wild ou /l\
Option facultative. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

/word ou /w\
Option facultative. Recherche uniquement les mots entiers.

## <a name="example"></a>Exemple
Cet exemple recherche le texte « btnCancel » dans tous les fichiers .cls situés dans le dossier « My Visual Studio Projects » et affiche les informations de correspondance dans la fenêtre Résultats de la recherche 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Voir aussi

- [Rechercher dans les fichiers](../../ide/find-in-files.md)
- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio, commandes](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
