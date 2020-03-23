---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567838"
---
# <a name="print-command"></a>Imprimer, commande

Évalue une expression ou affiche le texte spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Arguments

`text`

Obligatoire. Expression à évaluer ou texte à afficher.

## <a name="remarks"></a>Notes 

Vous pouvez utiliser le point d’interrogation (?) comme alias pour cette commande. Ainsi, la commande

```cmd
>Debug.Print expA
```

peut également être écrite

```cmd
? expA
```

Les deux versions de cette commande retournent la valeur actuelle de l’expression `expA`.

## <a name="example"></a> Exemple

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Voir aussi

- [Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)
- [Commandes de studio visuel](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Boîte de recherche/commande](../../ide/find-command-box.md)
- [Alias de commande de studio visuel](../../ide/reference/visual-studio-command-aliases.md)
