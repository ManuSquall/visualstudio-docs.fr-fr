---
title: Imprimer, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662158"
---
# <a name="print-command"></a>Imprimer, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Évalue une expression ou affiche le texte spécifié.

## <a name="syntax"></a>Syntaxe

```
Debug.Print text
```

## <a name="arguments"></a>Arguments
 `text` Obligatoire. Expression à évaluer ou texte à afficher.

## <a name="remarks"></a>Remarques
 Vous pouvez utiliser le point d’interrogation (?) comme alias pour cette commande. Ainsi, la commande

```
>Debug.Print expA
```

 peut également être écrite

```
>? expA
```

 Les deux versions de cette commande retournent la valeur courante de l’expression `expA`.

## <a name="example"></a>Exemples

```
>Debug.Print varA
```

## <a name="see-also"></a>Voir aussi
 [Commande évaluer les](../../ide/reference/evaluate-statement-command.md) [commandes Visual Studio commande Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
