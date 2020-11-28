---
title: Rechercher dans les fichiers, commande
description: Découvrez la commande find et comment elle recherche des fichiers à l’aide des options disponibles dans l’onglet Rechercher dans les fichiers de la fenêtre Rechercher et remplacer.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: aa0a907332b3ce0164573b809ee9c4b2ac2addda
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305389"
---
# <a name="find-in-files-command"></a>Rechercher dans les fichiers, commande
Recherche des fichiers en utilisant un sous-ensemble des options disponibles sous l’onglet **Rechercher dans les fichiers** de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments

`findwhat`\
Obligatoire. Texte à rechercher.

## <a name="switches"></a>Commutateurs
/case ou /c\
facultatif. Il y a correspondance uniquement si les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

/ext: `extensions`\
facultatif. Spécifie les extensions des fichiers dans lesquels effectuer la recherche. Si aucune extension n’est spécifiée, l’extension précédemment spécifiée est utilisée (le cas échéant).

/lookin: `searchpath`\
facultatif. Répertoire dans lequel effectuer une recherche. Si le chemin contient des espaces, placez le chemin complet entre guillemets.

/names ou /n\
facultatif. Affiche la liste des fichiers qui contiennent des correspondances.

/options ou /t\
facultatif. Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

/regex ou /r\
facultatif. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

/reset ou /e\
facultatif. Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

/stop\
facultatif. Arrête l’opération de recherche en cours, le cas échant. La recherche ignore tous les autres arguments si `/stop` est spécifié. Par exemple, pour arrêter la recherche en cours, entrez ce qui suit :

```cmd
>Edit.FindinFiles /stop
```

/sub ou /s\
facultatif. Recherche dans les sous-dossiers du répertoire qui est spécifié dans l’argument /lookin:`searchpath`.

/text2 ou /2\
facultatif. Affiche les résultats de la recherche dans la fenêtre Résultats de la recherche 2.

/wild ou /l\
facultatif. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

/word ou /w\
facultatif. Recherche uniquement les mots entiers.

## <a name="example"></a> Exemple
Cet exemple recherche le texte « btnCancel » dans tous les fichiers .cls situés dans le dossier « My Visual Studio Projects » et affiche les informations de correspondance dans la fenêtre Résultats de la recherche 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Voir aussi

- [Rechercher dans les fichiers](../../ide/find-in-files.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
