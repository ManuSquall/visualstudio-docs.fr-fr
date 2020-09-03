---
title: Commenter du code
description: Cet article décrit l’utilisation de commentaires dans l’éditeur de source de Visual Studio pour Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: a0aa3de91f1a2c75d73409d89f3cbc8894faacab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939120"
---
# <a name="comments"></a>Commentaires

Durant le débogage ou l’expérimentation du code, il peut être utile de commenter des blocs de code, de façon temporaire ou à long terme.

Pour marquer en commentaire tout un bloc de code :

* Sélectionnez le code et sélectionnez **Activer/désactiver le commentaire de ligne** dans le menu contextuel.

OR

* Utilisez la combinaison de touches `cmd + /` sur le code sélectionné.

Vous pouvez utiliser ces méthodes pour ajouter et supprimer des marques de commentaire dans les sections de code. Dans les fichiers C#, vous pouvez ajouter des niveaux supplémentaires de marques de commentaire de ligne, ce qui permet d’ajouter et de supprimer des marques de commentaire dans des parties du code, tout en conservant les commentaires déjà présents :

![commentaires multiniveaux](media/source-editor-image8.png)

Les commentaires sont également utiles pour documenter le code à l’attention des développeurs susceptibles d’intervenir dessus. Ils se présentent généralement sous la forme de commentaires multilignes, qui sont ajoutés de la façon suivante dans chaque langage :

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Voir aussi

- [Commenter du code (Visual Studio sur Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)