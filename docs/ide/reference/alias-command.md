---
title: Alias, commande
description: Découvrez comment utiliser la commande alias pour créer un alias pour une commande complète, une commande complète et des arguments, ou un autre alias.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8a9521809baf338c542b0c1cba288f643b985f02
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871507"
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
facultatif. Nom du nouvel alias. Si aucune valeur n’est fournie pour `aliasname`, la liste des alias en cours accompagnés de leur définition s’affiche.

`aliasstring`\
facultatif. Nom complet de la commande ou alias existant suivi des paramètres souhaités pour créer un alias. Si aucune valeur n’est fournie pour `aliasstring`, le nom et la chaîne associés à l’alias spécifié s’affichent.

## <a name="switches"></a>Commutateurs
/delete ou /del ou /d\
facultatif. Supprime l’alias spécifié, qui n’apparaît plus dans la liste de saisie semi-automatique.

/reset\
facultatif. Rétablit les paramètres d’origine de la liste d’alias prédéfinis. En d’autres termes, ce commutateur restaure tous les alias prédéfinis et supprime tous les alias définis par l’utilisateur.

## <a name="remarks"></a>Remarques
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

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
