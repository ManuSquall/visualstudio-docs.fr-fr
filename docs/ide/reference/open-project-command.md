---
title: Ouvrir un projet, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
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
ms.openlocfilehash: 0ff848ded38b0f59d3894ec4f78dd79ec9d182b8
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924146"
---
# <a name="open-project-command"></a>Ouvrir un projet, commande

Ouvre un projet existant ou une solution existante.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Arguments

`filename`

Obligatoire. Chemin complet et nom de fichier de la solution ou du projet à ouvrir.

> [!NOTE]
> La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.

## <a name="remarks"></a>Notes

La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

Cette commande n’est pas disponible lors du débogage.

## <a name="example"></a>Exemple

L’exemple suivant ouvre le projet Visual Basic **Test1** :

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Zone Rechercher/Commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)