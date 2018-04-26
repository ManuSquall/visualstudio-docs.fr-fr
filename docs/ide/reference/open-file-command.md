---
title: Ouvrir un fichier, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd75d32021f2dd3f6ac1ef76772ea30376ea1b8a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="open-file-command"></a>Ouvrir un fichier, commande
Ouvre un fichier existant et vous permet de spécifier un éditeur.

## <a name="syntax"></a>Syntaxe

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename`

 Obligatoire. Chemin complet ou partiel et nom du fichier à ouvrir. Les chemins comportant des espaces doivent être placés entre guillemets.

## <a name="switches"></a>Commutateurs
 /e:`editorname`

 Facultative. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.

 Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Notes
 La fonctionnalité de saisie semi-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.

## <a name="example"></a>Exemple
 Cet exemple ouvre la feuille de style « Test1.css » dans l’éditeur de code source.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Exécution, fenêtre](../../ide/reference/immediate-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)