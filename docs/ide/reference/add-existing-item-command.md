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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8ab2ce6e9f1260172bf0ffbf0aede9138a5115f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792621"
---
# <a name="add-existing-item-command"></a>Ajouter un élément existant, commande
Ajoute un fichier existant à la solution actuelle et l’ouvre.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` Obligatoire. Chemin complet et nom de fichier, avec l’extension, de l’élément à ajouter à la solution actuelle. Si le chemin ou le nom de fichier contient des espaces, placez le chemin complet entre guillemets.

## <a name="switches"></a>Commutateurs
 /e : `editorname` Facultatif. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la **boîte de dialogue Ouvrir avec**, entre guillemets. Par exemple, pour ouvrir une feuille de style dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Remarques
 La fonctionnalité de saisie semi-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.

## <a name="example"></a>Exemple
 Cet exemple ajoute le fichier Form1.frm à la solution actuelle.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)