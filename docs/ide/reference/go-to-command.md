---
title: Atteindre, commande
description: En savoir plus sur la commande atteindre et sur la façon dont elle déplace le curseur vers la ligne spécifiée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305213"
---
# <a name="go-to-command"></a>Atteindre, commande
Déplace le curseur à la ligne spécifiée.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
`linenumber`\
facultatif. Nombre entier représentant le numéro de la ligne à atteindre.

## <a name="remarks"></a>Remarques
La numérotation des lignes débute à 1. Si la valeur de `linenumber` est inférieure à 1, la première ligne est affichée. Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.

Si aucune valeur n’est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s’affiche.

L’alias de cette commande est GoToLn.

## <a name="example"></a>Exemple

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
