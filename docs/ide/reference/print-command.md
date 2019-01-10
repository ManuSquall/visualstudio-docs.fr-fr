---
title: Imprimer, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31f604d6df45cb22d18401b5925867d5ab0e02b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900884"
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