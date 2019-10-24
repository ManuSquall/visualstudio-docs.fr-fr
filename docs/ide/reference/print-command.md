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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae87afb11be71af8f0582a0b2899d67ba970186e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747824"
---
# <a name="print-command"></a>Imprimer (commande)

Évalue une expression ou affiche le texte spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Arguments

`text`

Requis. Expression à évaluer ou texte à afficher.

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

## <a name="example"></a>Exemple

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Voir aussi

- [Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)