---
title: Commentaires
description: Cet article décrit l’utilisation de commentaires dans l’éditeur de source de Visual Studio pour Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 4a7dfd0daaddad9f91d461689a0174469dd253c2
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
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
