---
title: Nouveau fichier, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671963"
---
# <a name="new-file-command"></a>Nouveau fichier, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crée un fichier et l’ouvre. Le fichier s’affiche sous le dossier Fichiers divers.

## <a name="syntax"></a>Syntaxe

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` Facultatif. Nom du fichier. Si aucun nom n’est fourni, un nom par défaut est utilisé. Si aucun nom de modèle n’est indiqué, un fichier texte est créé.

## <a name="switches"></a>Commutateurs
 /t:`templatename` (facultatif). Spécifie le type de fichier à créer.

 La syntaxe de l’argument /t:`templatename` reflète les informations de la boîte de dialogue Nouveau fichier. Entrez le nom de la catégorie suivi d’une barre oblique inverse (`\`) et du nom du modèle, et placez la chaîne entière entre guillemets.

 Par exemple, pour créer un fichier source [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], entrez les informations suivantes pour l’argument /t:`templatename`.

```
/t:"Visual C++\C++ File (.cpp)"
```

 L’exemple ci-dessus indique que le modèle de fichier C++ se trouve sous la catégorie Visual C++ dans la boîte de dialogue **Nouveau fichier**.

 /e:`editorname` (facultatif). Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.

 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.

 Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Exemples
 Cet exemple crée une page web « test1.htm » et l’ouvre dans l’éditeur de code source.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Voir aussi
 [Commande](../../ide/reference/command-window.md) [Visual Studio commandes](../../ide/reference/visual-studio-commands.md) fenêtre [exécution fenêtre exécution](../../ide/reference/immediate-window.md) [Rechercher/zone de commandes](../../ide/find-command-box.md) [Visual Studio alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
