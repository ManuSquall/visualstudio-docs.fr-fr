---
title: Atteindre, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5782f5e7dba8d18f9d6f48f345d5e133138e6eea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748750"
---
# <a name="go-to-command"></a>Atteindre, commande
Déplace le curseur à la ligne spécifiée.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
`linenumber`\
Optionnel. Nombre entier représentant le numéro de la ligne à atteindre.

## <a name="remarks"></a>Notes
La numérotation des lignes débute à 1. Si la valeur de `linenumber` est inférieure à 1, la première ligne est affichée. Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.

Si aucune valeur n’est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s’affiche.

L’alias de cette commande est GoToLn.

## <a name="example"></a>Exemple

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)