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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb6bfc98d5ef6f7b3d3b6291ea55530325836d56
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918960"
---
# <a name="shell-command"></a>Shell, commande
Lance les programmes exécutables à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Arguments
`path`

Obligatoire. Chemin et nom du fichier à exécuter ou du document à ouvrir. Un chemin complet est requis si le fichier spécifié ne se trouve pas dans l’un des répertoires figurant dans la variable d’environnement PATH.

`args`

facultatif. Arguments à passer au programme appelé.

## <a name="switches"></a>Commutateurs
/commandwindow [ou] /command [ou] /c [ou] /cmd

facultatif. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Commande**.

/dir:`folder` [ou] /d: `folder`

facultatif. Spécifie le répertoire de travail à définir quand le programme est exécuté.

/outputwindow [ou] /output [ou] /out [ou] /o

facultatif. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Sortie**.

## <a name="remarks"></a>Remarques
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

## <a name="example"></a>Exemples
La commande suivante utilise xcopy.exe pour copier le fichier `MyText.txt` dans le dossier `Text`. La sortie de xcopy.exe s’affiche à la fois dans la fenêtre **Commande** et dans la fenêtre **Sortie**.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Sortie (fenêtre)](../../ide/reference/output-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)