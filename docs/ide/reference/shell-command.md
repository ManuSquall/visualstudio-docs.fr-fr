---
title: Shell, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 502bb7b1ab6236fd88c7c6dbc789737e50686d89
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747740"
---
# <a name="shell-command"></a>Shell, commande
Lance les programmes exécutables à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Arguments
`path`

Requis. Chemin et nom du fichier à exécuter ou du document à ouvrir. Un chemin complet est requis si le fichier spécifié ne se trouve pas dans l’un des répertoires figurant dans la variable d’environnement PATH.

`args`

Optionnel. Arguments à passer au programme appelé.

## <a name="switches"></a>Commutateurs
/commandwindow [ou] /command [ou] /c [ou] /cmd

Optionnel. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Commande**.

/dir:`folder` [ou] /d: `folder`

Optionnel. Spécifie le répertoire de travail à définir quand le programme est exécuté.

/outputwindow [ou] /output [ou] /out [ou] /o

Optionnel. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Sortie**.

## <a name="remarks"></a>Notes
Les commutateurs /dir /o /c doivent être spécifiés immédiatement après `Tools.Shell`. Toute syntaxe spécifiée après le nom de l’exécutable est transmise en tant qu’argument de la ligne de commande.

L’alias prédéfini `Shell` peut être utilisé à la place de `Tools.Shell`.

> [!CAUTION]
> Si l’argument `path` fournit le chemin du répertoire et le nom du fichier, vous devez placer le nom de chemin tout entier entre guillemets ("""), comme dans l’exemple suivant :

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Chaque groupe de trois guillemets (""") est interprété par le processeur `Shell` comme un seul caractère de guillemet. Ainsi, l’exemple précédent passe en fait la chaîne de chemin suivante à la commande `Shell` :

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Si vous ne mettez pas la chaîne de chemin entre guillemets ("""), Windows utilisera uniquement la partie de la chaîne jusqu’au premier espace. Par exemple, si la chaîne de chemin ci-dessus n’a pas été correctement mise entre guillemets, Windows recherche un fichier nommé « Program » situé dans le répertoire racine C:\. Si un fichier exécutable C:\Program.exe est effectivement disponible, même installé de manière illicite, Windows essaie d’exécuter ce programme à la place du programme « C:\Program Files\SomeFile.exe » voulu.

## <a name="example"></a>Exemple
La commande suivante utilise xcopy.exe pour copier le fichier `MyText.txt` dans le dossier `Text`. La sortie de xcopy.exe s’affiche à la fois dans la fenêtre **Commande** et dans la fenêtre **Sortie**.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Sortie, fenêtre](../../ide/reference/output-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)