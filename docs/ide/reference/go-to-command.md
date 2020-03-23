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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569203"
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

## <a name="remarks"></a>Notes 
La numérotation des lignes débute à 1. Si la valeur de `linenumber` est inférieure à 1, la première ligne est affichée. Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.

Si aucune valeur n’est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s’affiche.

L’alias de cette commande est GoToLn.

## <a name="example"></a> Exemple

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Voir aussi

- [Commandes de studio visuel](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Boîte de recherche/commande](../../ide/find-command-box.md)
- [Alias de commande de studio visuel](../../ide/reference/visual-studio-command-aliases.md)
