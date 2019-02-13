---
title: Espion express, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e45a6c63cb1f886c1440b93d58f944458f61290
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55969865"
---
# <a name="quick-watch-command"></a>Espion express, commande
Affiche le texte sélectionné ou spécifié dans le champ Expression de la fenêtre [Espion express](../../debugger/watch-and-quickwatch-windows.md). Vous pouvez utiliser cette boîte de dialogue pour calculer la valeur actuelle d’une variable ou d’une expression reconnue par le débogueur, ou le contenu d’un Registre. Vous pouvez aussi modifier la valeur de toute variable non constante ou le contenu de tout Registre.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments
 `text`

 Optionnel. Texte à ajouter à la boîte de dialogue **Espion express**.

## <a name="remarks"></a>Notes
 Si l’argument `text` est omis, le texte ou mot sélectionné au niveau du curseur est ajouté dans la fenêtre Espion.

## <a name="example"></a>Exemple

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Voir aussi

- [Définir un espion sur les variables à l’aide des fenêtres Espion et Espion express dans Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)