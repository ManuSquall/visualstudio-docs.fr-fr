---
title: Nouveau fichier, commande
description: Découvrez la nouvelle commande de fichier et comment elle crée un nouveau fichier et l’ouvre.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c800ce0ed130ed78f9537584c95a29a717f405fa
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304101"
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

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Fenêtre exécution](../../ide/reference/immediate-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
