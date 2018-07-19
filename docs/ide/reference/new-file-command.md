---
title: Nouveau fichier, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a519de555f35df4fac91a9960993a0f163c4de5a
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704744"
---
# <a name="new-file-command"></a>Nouveau fichier, commande
Crée un fichier et l’ouvre. Le fichier s’affiche sous le dossier Fichiers divers.

## <a name="syntax"></a>Syntaxe

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
 `filename`

 Facultative. Nom du fichier. Si aucun nom n’est fourni, un nom par défaut est utilisé. Si aucun nom de modèle n’est indiqué, un fichier texte est créé.

## <a name="switches"></a>Commutateurs
 /t:`templatename`

 Facultative. Spécifie le type de fichier à créer.

 La syntaxe de l’argument /t:`templatename` reflète les informations de la boîte de dialogue Nouveau fichier. Entrez le nom de la catégorie suivi d’une barre oblique inverse (`\`) et du nom du modèle, et placez la chaîne entière entre guillemets.

 Par exemple, pour créer un fichier source [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], entrez les informations suivantes pour l’argument /t:`templatename`.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

 L’exemple ci-dessus indique que le modèle de fichier C++ se trouve sous la catégorie Visual C++ dans la boîte de dialogue **Nouveau fichier**.

 /e:`editorname`

 Facultative. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.

 Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Exemple
 Cet exemple crée une page web « test1.htm » et l’ouvre dans l’éditeur de code source.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Exécution, fenêtre](../../ide/reference/immediate-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)