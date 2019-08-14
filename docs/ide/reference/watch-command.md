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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac779dc902a331a45b600113a11db5364293f74
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925947"
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

## <a name="remarks"></a>Remarques

La valeur d’`index` doit être un entier. Les valeurs valides sont 1, 2, 3 ou 4.

## <a name="example"></a>Exemples

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Voir aussi

- [Fenêtres Variables locales et Automatique](../../debugger/autos-and-locals-windows.md)
- [Définir un espion sur les variables à l’aide des fenêtres Espion et Espion express dans Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)