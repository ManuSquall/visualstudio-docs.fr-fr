---
title: Nouveau fichier, commande
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe8a99ee59a347fdcb7cff601b75139760630f7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595954"
---
# <a name="new-file-command"></a>Nouveau fichier, commande
Crée un fichier et l’ouvre. Le fichier s’affiche sous le dossier Fichiers divers.

## <a name="syntax"></a>Syntaxe

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
`filename`

facultatif. Nom du fichier. Si aucun nom n’est fourni, un nom par défaut est utilisé. Si aucun nom de modèle n’est indiqué, un fichier texte est créé.

## <a name="switches"></a>Commutateurs
/t:`templatename`\
facultatif. Spécifie le type de fichier à créer.

La syntaxe de l’argument /t:`templatename` reflète les informations de la boîte de dialogue Nouveau fichier. Entrez le nom de la catégorie suivi d’une barre oblique inverse (`\`) et du nom du modèle, et placez la chaîne entière entre guillemets.

Par exemple, pour créer un fichier source [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], entrez les informations suivantes pour l’argument /t:`templatename`.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

L’exemple ci-dessus indique que le modèle de fichier C++ se trouve sous la catégorie Visual C++ dans la boîte de dialogue **Nouveau fichier**.

/e:`editorname`\
facultatif. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.

Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a> Exemple
Cet exemple crée une page web « test1.htm » et l’ouvre dans l’éditeur de code source.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Voir aussi

- [Commandes de studio visuel](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Fenêtre Exécution](../../ide/reference/immediate-window.md)
- [Boîte de recherche/commande](../../ide/find-command-box.md)
- [Alias de commande de studio visuel](../../ide/reference/visual-studio-command-aliases.md)
