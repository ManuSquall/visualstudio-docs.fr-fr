---
title: Ouvrir un projet, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>Ouvrir un projet, commande
Ouvre un projet existant.

## <a name="syntax"></a>Syntaxe

```
File.OpenProject filename
```

## <a name="arguments"></a>Arguments
 `filename`

 Obligatoire. Chemin complet et nom de fichier du projet à ouvrir.

 La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.

## <a name="remarks"></a>Notes
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

 Cette commande n’est pas disponible lors du débogage.

## <a name="example"></a>Exemple
 Cet exemple ouvre le projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)