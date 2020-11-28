---
title: Enregistrer la sortie de la fenêtre de commande, commande
description: En savoir plus sur la commande Enregistrer la sortie de la fenêtre commande et la façon dont elle copie toutes les entrées et sorties de la Fenêtre Commande dans un fichier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cab4f102832e8dfa6ce51b61abed8e3bfd672c40
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305268"
---
# <a name="log-command-window-output-command"></a>Enregistrer la sortie de la fenêtre Commande, commande

Copie toutes les entrées et sorties de la fenêtre **commande** dans un fichier.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Arguments

`filename`\
facultatif. Nom du fichier journal. Par défaut, le fichier est créé dans le dossier du profil de l’utilisateur. Si le nom de fichier existe déjà, le journal est ajouté à la fin du fichier existant. Si aucun fichier n’est spécifié, le dernier fichier spécifié est utilisé. Si aucun fichier n’a été spécifié précédemment, le fichier journal cmdline.log est créé par défaut.

> [!TIP]
> Pour modifier l’emplacement d’enregistrement du fichier journal, entrez le chemin complet du fichier, en l’entourant de guillemets s’il comporte des espaces.

## <a name="switches"></a>Commutateurs

/on\
facultatif. Démarre le journal pour la fenêtre **Commande** dans le fichier spécifié et ajoute les nouvelles informations à la fin de ce fichier.

/off\
facultatif. Arrête le journal pour la fenêtre **Commande**.

/overwrite\
facultatif. Si le fichier spécifié dans l’argument `filename` est identique à un fichier existant, celui-ci est remplacé.

## <a name="remarks"></a>Remarques

Si aucun fichier n’est spécifié, le fichier cmdline.log est créé par défaut. L’alias par défaut de cette commande est Log.

## <a name="examples"></a>Exemples

Cet exemple crée le fichier journal cmdlog, puis démarre l’enregistrement des commandes.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Cet exemple arrête l’enregistrement des commandes.

```cmd
>Tools.LogCommandWindowOutput /off
```

Cet exemple reprend l’enregistrement des commandes dans le dernier fichier journal utilisé.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre Commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
