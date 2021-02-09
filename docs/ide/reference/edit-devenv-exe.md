---
title: -Edit (devenv.exe)
description: Découvrez comment utiliser le commutateur de ligne de commande Edit devenv pour ouvrir un fichier spécifié dans une instance existante de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45d0b1342ea0e53c4897881ebb5cfee0a7241d6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882073"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Ouvre le fichier spécifié dans une instance existante de Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *File1*

  Facultatif. Fichier à ouvrir dans une instance existante de Visual Studio. S’il n’en existe pas, une instance est créée avec une disposition de fenêtre simplifiée ; l’outil ouvre *File1* dans cette nouvelle instance.

- *FileN*

  Facultatif. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de Visual Studio.

## <a name="remarks"></a>Remarques

Si aucun fichier n’est spécifié, une instance existante de Visual Studio reçoit le focus. S’il n’existe pas non plus d’instances de Visual Studio, l’outil crée une instance avec une disposition de fenêtre simplifiée.

Si l’instance existante de Visual Studio est dans un état modal, le fichier s’ouvre dans l’instance existante lorsque Visual Studio quitte l’état modal. Cette situation peut par exemple se produire lorsque la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte.

Si plusieurs instances de Visual Studio sont ouvertes, le fichier est ouvert dans l’instance la plus récemment ouverte.

## <a name="example"></a>Exemple

Le premier exemple ouvre le fichier `MyFile.cs` dans une instance existante de Visual Studio. S’il n’en existe pas, l’outil ouvre le fichier dans une nouvelle instance. Le second exemple est similaire, à ceci près qu’il ouvre trois fichiers au lieu d’un seul.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
