---
title: Debug.Print
description: En savoir plus sur la commande Print et sur la manière dont elle évalue une expression ou affiche le texte spécifié.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0524ce015ea4675254615c11e5768e59049c37f6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304127"
---
# <a name="print-command"></a>Imprimer (commande)

Évalue une expression ou affiche le texte spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Arguments

`text`

Obligatoire. Expression à évaluer ou texte à afficher.

## <a name="remarks"></a>Remarques

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
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
