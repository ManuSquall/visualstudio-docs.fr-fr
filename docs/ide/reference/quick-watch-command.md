---
title: Espion express, commande
description: En savoir plus sur la commande espion rapide et la façon dont elle affiche le texte sélectionné ou spécifié dans le champ expression de la fenêtre Espion express.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6185418364e8b22e1f473308b2db9899c8778d13
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304162"
---
# <a name="quick-watch-command"></a>Espion express, commande
Affiche le texte sélectionné ou spécifié dans le champ Expression de la fenêtre [Espion express](../../debugger/watch-and-quickwatch-windows.md). Vous pouvez utiliser cette boîte de dialogue pour calculer la valeur actuelle d’une variable ou d’une expression reconnue par le débogueur, ou le contenu d’un Registre. Vous pouvez aussi modifier la valeur de toute variable non constante ou le contenu de tout Registre.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments

`text`\
facultatif. Texte à ajouter à la boîte de dialogue **Espion express**.

## <a name="remarks"></a>Remarques

Si l’argument `text` est omis, le texte ou mot sélectionné au niveau du curseur est ajouté dans la fenêtre Espion.

## <a name="example"></a>Exemple

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Voir aussi

- [Définir un espion sur les variables à l’aide des fenêtres Espion et Espion express dans Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
