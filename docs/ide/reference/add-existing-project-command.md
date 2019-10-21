---
title: Ajouter un projet existant, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6aca05758185f4df47688044f479b7bbe2829e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658818"
---
# <a name="add-existing-project-command"></a>Ajouter un projet existant, commande
Ajoute un projet existant à la solution actuelle.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
`filename`\
Optionnel. Chemin complet et nom (extension comprise) du projet à ajouter à la solution.

Si l’argument `filename` comprend des espaces, il doit être placé entre guillemets.

Si aucun nom de fichier n’est spécifié, la commande ouvre la boîte de dialogue Fichier pour que l’utilisateur puisse sélectionner un projet.

## <a name="remarks"></a>Notes
La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

## <a name="example"></a>Exemple
Cet exemple ajoute le projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (TestProject1) à la solution actuelle.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)