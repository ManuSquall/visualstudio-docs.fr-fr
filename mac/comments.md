---
title: Commentaires
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 0d49896a3c265dfdc5a25c46e80de498adfffb07
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="comments"></a>Commentaires

Lors du débogage ou de l’expérimentation du code, il peut être utile de marquer en commentaire des blocs de code, de façon temporaire ou définitive. 

Pour marquer en commentaire tout un bloc de code :

* Sélectionnez le code et sélectionnez **Activer/désactiver le commentaire de ligne** dans le menu contextuel.

OU

* Utilisez la combinaison de touches `cmd + /` sur le code sélectionné.

Vous pouvez utiliser ces méthodes pour ajouter et supprimer des marques de commentaire dans les sections de code. Dans les fichiers C#, vous pouvez ajouter des niveaux supplémentaires de marques de commentaire de ligne, ce qui permet d’ajouter et de supprimer des marques de commentaire dans des parties du code, tout en conservant les commentaires déjà présents : 

 ![commentaires multiniveaux](media/source-editor-image8.png)

Les commentaires sont également utiles pour documenter le code à l’attention des développeurs susceptibles d’intervenir dessus. Ils se présentent généralement sous la forme de commentaires multilignes, qui sont ajoutés de la façon suivante dans chaque langage :

**C#**

``` cs
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
