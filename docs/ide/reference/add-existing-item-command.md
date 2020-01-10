---
title: Ajouter un élément existant, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d49f0fde7bbf13a1219296420b84970f4350860
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585702"
---
# <a name="add-existing-item-command"></a>Ajouter un élément existant, commande
Ajoute un fichier existant à la solution actuelle et l’ouvre.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
`filename`\
Requis. Chemin complet et nom de fichier, avec l’extension, de l’élément à ajouter à la solution actuelle. Si le chemin ou le nom de fichier contient des espaces, placez le chemin complet entre guillemets.

## <a name="switches"></a>Commutateurs
/e: `editorname`\
Option facultative. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la **boîte de dialogue Ouvrir avec**, entre guillemets. Par exemple, pour ouvrir une feuille de style dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Notes
La fonctionnalité de saisie semi-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.

## <a name="example"></a>Exemple
Cet exemple ajoute le fichier Form1.frm à la solution actuelle.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Voir aussi

- [Visual Studio, commandes](../../ide/reference/visual-studio-commands.md)
- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
