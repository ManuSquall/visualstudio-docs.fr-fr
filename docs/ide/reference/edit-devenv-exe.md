---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb5ae37d3e4dc0973320c68f9db169cdbf7d663a
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227679"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Ouvre le fichier spécifié dans une instance existante de Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *File1*

  Optionnel. Fichier à ouvrir dans une instance existante de Visual Studio. S’il n’en existe pas, une instance est créée avec une disposition de fenêtre simplifiée ; l’outil ouvre *File1* dans cette nouvelle instance.

- *FileN*

  Optionnel. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de Visual Studio.

## <a name="remarks"></a>Notes

Si aucun fichier n’est spécifié, une instance existante de Visual Studio reçoit le focus. S’il n’existe pas non plus d’instances de Visual Studio, l’outil crée une instance avec une disposition de fenêtre simplifiée.

Si l’instance existante de Visual Studio est dans un état modal, le fichier s’ouvre dans l’instance existante lorsque Visual Studio quitte l’état modal. Cette situation peut par exemple se produire lorsque la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte.

## <a name="example"></a>Exemple

Le premier exemple ouvre le fichier `MyFile.cs` dans une instance existante de Visual Studio. S’il n’en existe pas, l’outil ouvre le fichier dans une nouvelle instance. Le second exemple est similaire, à ceci près qu’il ouvre trois fichiers au lieu d’un seul.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)