---
title: Ajouter un projet existant, commande
description: En savoir plus sur la commande Ajouter un projet existant et sur la façon dont elle ajoute un projet existant à une solution actuelle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c12106621599d428e9a701de9ba5e468b5e312a
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871000"
---
# <a name="add-existing-project-command"></a>Ajouter un projet existant, commande
Ajoute un projet existant à la solution actuelle.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
`filename`\
facultatif. Chemin complet et nom (extension comprise) du projet à ajouter à la solution.

Si l’argument `filename` comprend des espaces, il doit être placé entre guillemets.

Si aucun nom de fichier n’est spécifié, la commande ouvre la boîte de dialogue Fichier pour que l’utilisateur puisse sélectionner un projet.

## <a name="remarks"></a>Remarques
La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

## <a name="example"></a>Exemple
Cet exemple ajoute le projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (TestProject1) à la solution actuelle.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
