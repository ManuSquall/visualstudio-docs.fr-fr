---
title: Shell, commande
description: En savoir plus sur la commande shell et son lancement des programmes exécutables à partir de Visual Studio.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b520d3bedf31bc09dc0cf48e86777872176e2e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957619"
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

Facultatif. Arguments à passer au programme appelé.

## <a name="switches"></a>Commutateurs
/commandwindow [ou] /command [ou] /c [ou] /cmd

Facultatif. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Commande**.

/dir:`folder` [ou] /d: `folder`

Facultatif. Spécifie le répertoire de travail à définir quand le programme est exécuté.

/outputwindow [ou] /output [ou] /out [ou] /o

Facultatif. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Sortie**.

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
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Fenêtre Sortie](../../ide/reference/output-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
