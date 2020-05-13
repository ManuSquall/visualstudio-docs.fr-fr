---
title: Ouvrir un fichier, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50e29e3182a19c9f3a667d41725327110b415fd0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591513"
---
# <a name="open-file-command"></a>Ouvrir un fichier, commande

Ouvre un fichier existant et vous permet de spécifier un éditeur.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments

`filename`

Obligatoire. Chemin complet ou partiel et nom du fichier à ouvrir. Les chemins comportant des espaces doivent être placés entre guillemets.

## <a name="switches"></a>Commutateurs

/e:`editorname`

facultatif. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.

Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Notes 

La fonctionnalité de saisie semi-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.

## <a name="example"></a> Exemple

Cet exemple ouvre la feuille de style « Test1.css » dans l’éditeur de code source.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre de commande](../../ide/reference/command-window.md)
- [Fenêtre immédiate](../../ide/reference/immediate-window.md)
- [Boîte De recherche/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
