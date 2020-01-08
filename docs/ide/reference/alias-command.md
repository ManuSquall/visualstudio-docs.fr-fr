---
title: Alias, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 031f1a4bab1acee3f3d0999b17c0b607f7808df9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596903"
---
# <a name="alias-command"></a>Alias, commande
Crée un alias pour une commande complète, pour une commande complète et des arguments ou pour un autre alias.

> [!TIP]
> Tapez `>alias` sans aucun argument pour afficher la liste actuelle des alias et leur définition.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
`aliasname`\
Option facultative. Nom du nouvel alias. Si aucune valeur n’est fournie pour `aliasname`, la liste des alias en cours accompagnés de leur définition s’affiche.

`aliasstring`\
Option facultative. Nom complet de la commande ou alias existant suivi des paramètres souhaités pour créer un alias. Si aucune valeur n’est fournie pour `aliasstring`, le nom et la chaîne associés à l’alias spécifié s’affichent.

## <a name="switches"></a>Commutateurs
/delete ou /del ou /d\
Option facultative. Supprime l’alias spécifié, qui n’apparaît plus dans la liste de saisie semi-automatique.

/reset\
Option facultative. Rétablit les paramètres d’origine de la liste d’alias prédéfinis. En d’autres termes, ce commutateur restaure tous les alias prédéfinis et supprime tous les alias définis par l’utilisateur.

## <a name="remarks"></a>Notes
Dans la mesure où un alias représente des commandes, il doit être placé au début de la ligne de commande.

Lors de l’émission de cette commande, vous devez inclure les commutateurs immédiatement après la commande, et non après les alias, sans quoi le commutateur lui-même sera inclus dans la chaîne de l’alias.

Le commutateur `/reset` demande confirmation avant de restaurer les alias. Il n’existe pas de forme abrégée de `/reset`.

## <a name="examples"></a>Exemples
Cet exemple crée un alias, `upper`, pour la commande Edit.MakeUpperCase complète.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Cet exemple supprime l’alias `upper`.

```cmd
>Tools.alias /delete upper
```

Cet exemple affiche la liste de tous les alias en cours accompagnés de leur définition.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Voir aussi

- [Visual Studio, commandes](../../ide/reference/visual-studio-commands.md)
- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
