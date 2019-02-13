---
title: Imprimer, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9a3de1fba86c78f16703efd858448bc0f25e8d0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952292"
---
# <a name="print-command"></a>Imprimer, commande
Évalue une expression ou affiche le texte spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Print text
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
>? expA
```

 Les deux versions de cette commande retournent la valeur courante de l’expression `expA`.

## <a name="example"></a>Exemple

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>Voir aussi

- [Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)