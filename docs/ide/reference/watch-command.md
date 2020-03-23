---
title: Espion, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7c89761dfc12d342747567389e39daeed4a227
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585650"
---
# <a name="watch-command"></a>Espion, commande
Crée et ouvre une instance spécifiée d’une fenêtre **Espion** . Vous pouvez utiliser une fenêtre **Espion** pour calculer les valeurs des variables, des expressions et des registres, modifier ces valeurs et enregistrer les résultats.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Arguments

`index`\
Obligatoire. Numéro d’instance de la fenêtre Espion.

## <a name="remarks"></a>Notes 

La valeur d’`index` doit être un entier. Les valeurs valides sont 1, 2, 3 ou 4.

## <a name="example"></a> Exemple

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Voir aussi

- [Fenêtres Variables locales et Automatique](../../debugger/autos-and-locals-windows.md)
- [Définir un espion sur les variables à l’aide des fenêtres Espion et Espion express dans Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Commandes de studio visuel](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Boîte de recherche/commande](../../ide/find-command-box.md)
- [Alias de commande de studio visuel](../../ide/reference/visual-studio-command-aliases.md)
