---
title: Ouvrir un projet (commande)
description: En savoir plus sur la commande ouvrir un projet et sur son mode d’ouverture d’une solution ou d’un projet existant.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce00713cbfe862c5788a0131c99ba4c5750bb600
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304142"
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

## <a name="remarks"></a>Remarques

La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

Cette commande n’est pas disponible lors du débogage.

## <a name="example"></a> Exemple

L’exemple suivant ouvre le projet Visual Basic **Test1** :

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
