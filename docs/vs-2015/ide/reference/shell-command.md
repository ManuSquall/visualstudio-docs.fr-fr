---
title: Shell, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ad49aadf6be56fb330b883050e6a6ff893cf054a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663543"
---
# <a name="shell-command"></a>Shell, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lance les programmes exécutables à partir de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntaxe

```
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Arguments
 `path` Obligatoire. Chemin et nom du fichier à exécuter ou du document à ouvrir. Un chemin complet est requis si le fichier spécifié ne se trouve pas dans l’un des répertoires figurant dans la variable d’environnement PATH.

 `args` Facultatif. Arguments à passer au programme appelé.

## <a name="switches"></a>Commutateurs
 /CommandWindow [ou]/Command [ou]/c [ou]/cmd facultatif. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Commande**.

 /dir : `folder` [ou]/d : `folder` facultatif. Spécifie le répertoire de travail à définir quand le programme est exécuté.

 /OutputWindow [ou]/output [ou]/out [ou]/o facultatif. Spécifie que la sortie pour l’exécutable doit s’afficher dans la fenêtre **Sortie**.

## <a name="remarks"></a>Remarques
 Les commutateurs /dir /o /c doivent être spécifiés immédiatement après `Tools.Shell`. Toute syntaxe spécifiée après le nom de l’exécutable est transmise en tant qu’argument de la ligne de commande.

 L’alias prédéfini `Shell` peut être utilisé à la place de `Tools.Shell`.

> [!CAUTION]
> Si l’argument `path` fournit le chemin du répertoire et le nom du fichier, vous devez placer le nom de chemin tout entier entre guillemets ("""), comme dans l’exemple suivant :

```
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Chaque groupe de trois guillemets (""") est interprété par le processeur `Shell` comme un seul caractère de guillemet. Ainsi, l’exemple précédent passe en fait la chaîne de chemin suivante à la commande `Shell` :

```
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Si vous ne mettez pas la chaîne de chemin entre guillemets ("""), Windows utilisera uniquement la partie de la chaîne jusqu’au premier espace. Par exemple, si la chaîne de chemin ci-dessus n’a pas été correctement mise entre guillemets, Windows recherche un fichier nommé « Program » situé dans le répertoire racine C:\. Si un fichier exécutable C:\Program.exe est effectivement disponible, même installé de manière illicite, Windows essaie d’exécuter ce programme à la place du programme « C:\Program Files\SomeFile.exe » voulu.

## <a name="example"></a>Exemples
 La commande suivante utilise xcopy.exe pour copier le fichier `MyText.txt` dans le dossier `Text`. La sortie de xcopy.exe s’affiche à la fois dans la fenêtre **Commande** et dans la fenêtre **Sortie**.

```
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Voir aussi
 [Fenêtre de commande](../../ide/reference/command-window.md) des [commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre Sortie](../../ide/reference/output-window.md) les [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md) de [la zone Rechercher/commande](../../ide/find-command-box.md)
