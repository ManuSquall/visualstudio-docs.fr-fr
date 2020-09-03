---
title: Remplacer, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665627"
---
# <a name="replace-command"></a>Remplacer, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Remplace le texte dans les fichiers à l’aide d’un sous-ensemble des options proposées sous l’onglet **Remplacer dans les fichiers** de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` Obligatoire. Texte à rechercher.

 `replacewith` Obligatoire. Texte de remplacement du texte trouvé.

## <a name="switches"></a>Commutateurs
 /All ou/a facultatif. Remplace toutes les occurrences du texte recherché par le texte de remplacement.

 /case ou /c (facultatif). Il y a correspondance uniquement quand les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

 /doc ou /d (facultatif). Effectue la recherche uniquement dans le document actif. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /Hidden ou/h facultatif. Recherche le texte masqué et réduit, par exemple les métadonnées d’un contrôle DTC, une zone masquée du plan d’un document ou encore une classe ou une méthode réduite.

 /open ou /o (facultatif). Effectue la recherche dans tous les documents ouverts comme s’il s’agissait d’un document unique. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /options ou /t (facultatif). Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

 /proc ou /p (facultatif). Effectue la recherche uniquement dans la procédure en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /regex ou /r (facultatif). Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset ou /e (facultatif). Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

 /sel ou /s (facultatif). Effectue la recherche uniquement dans la sélection en cours. Spécifiez une seule des étendues de recherche disponibles, à savoir `/doc`, `/proc`, `/open` ou `/sel`.

 /up ou /u (facultatif). Effectue la recherche à partir de l’emplacement actuel vers le début du fichier. Par défaut, les recherches commencent à l’emplacement actuel dans le fichier et s’effectuent vers la fin du fichier.

 /wild ou /l (facultatif). Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

 /word ou /w (facultatif). Recherche uniquement les mots entiers.

## <a name="example"></a>Exemple
 Cet exemple remplace `btnSend` par `btnSubmit` dans tous les documents ouverts.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Voir aussi
 [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md) [fenêtre de commandes](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [Visual Studio commandes](../../ide/reference/visual-studio-commands.md) Visual [Studio alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
