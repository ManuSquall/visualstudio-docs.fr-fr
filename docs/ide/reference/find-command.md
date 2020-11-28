---
title: Rechercher, commande
description: En savoir plus sur la commande find et sur la manière dont elle effectue une recherche dans les fichiers à l’aide d’un sous-ensemble des options disponibles sous l’onglet Rechercher dans les fichiers de la fenêtre Rechercher et remplacer.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 886695cea38909a8efa74797391adb1b6dd97d19
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305403"
---
# <a name="find-command"></a>Rechercher, commande
Recherche des fichiers en utilisant un sous-ensemble des options disponibles sous l’onglet **Rechercher dans les fichiers** de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Arguments
`findwhat` Obligatoire. Texte à rechercher.

## <a name="switches"></a>Commutateurs
/case ou /c\
facultatif. Il y a correspondance uniquement si les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

/doc ou /d\
facultatif. Effectue la recherche uniquement dans le document actif. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/markall ou /m\
facultatif. Ajoute un graphique à chaque ligne contenant une correspondance du texte recherché dans le document actif.

/open ou /o\
facultatif. Effectue la recherche dans tous les documents ouverts comme s’il s’agissait d’un document unique. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/options ou /t\
facultatif. Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

/proc ou /p\
facultatif. Effectue la recherche uniquement dans la procédure en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/reset ou /e\
facultatif. Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

/sel ou /s\
facultatif. Effectue la recherche uniquement dans la sélection en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

/up ou /u\
facultatif. Effectue la recherche à partir de l’emplacement actuel vers le début du fichier. Par défaut, les recherches commencent à l’emplacement actuel dans le fichier et s’effectuent vers la fin du fichier.

/regex ou /r\
facultatif. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

/wild ou /l\
facultatif. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

/word ou /w\
facultatif. Recherche uniquement les mots entiers.

## <a name="example"></a> Exemple
Cet exemple recherche le mot « somestring » en respectant la casse dans la section de code sélectionnée.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Voir aussi

- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
