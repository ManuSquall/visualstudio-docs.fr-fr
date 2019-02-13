---
title: Enregistrer la sortie de la fenêtre de commande, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588c5e39f8b6b6a89de1636bd45036b21d392d33
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930530"
---
# <a name="log-command-window-output-command"></a>Enregistrer la sortie de la fenêtre de commande, commande
Copie toutes les entrées et sorties de la fenêtre **Commande** dans un fichier.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Arguments
 `filename`

 Optionnel. Nom du fichier journal. Par défaut, le fichier est créé dans le dossier du profil de l’utilisateur. Si le nom de fichier existe déjà, le journal est ajouté à la fin du fichier existant. Si aucun fichier n’est spécifié, le dernier fichier spécifié est utilisé. Si aucun fichier n’a été spécifié précédemment, le fichier journal cmdline.log est créé par défaut.

> [!TIP]
> Pour modifier l’emplacement d’enregistrement du fichier journal, entrez le chemin complet du fichier, en l’entourant de guillemets s’il comporte des espaces.


## <a name="switches"></a>Commutateurs
 /on

 Optionnel. Démarre le journal pour la fenêtre **Commande** dans le fichier spécifié et ajoute les nouvelles informations à la fin de ce fichier.

 /off

 Optionnel. Arrête le journal pour la fenêtre **Commande**.

 /overwrite

 Optionnel. Si le fichier spécifié dans l’argument `filename` est identique à un fichier existant, celui-ci est remplacé.

## <a name="remarks"></a>Notes
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
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)