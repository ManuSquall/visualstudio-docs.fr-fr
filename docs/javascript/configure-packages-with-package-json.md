---
title: Configurer des packages npm avec package.json
description: Spécifier les versions de package npm avec package.json
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f2712545659d66b421de78d8f8835a613563fdd0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857090"
---
# <a name="packagejson-configuration"></a>Configuration de package.json

Si vous développez une application Node.js avec un grand nombre de packages npm, il n’est pas rare de rencontrer des avertissements ou erreurs quand vous générez votre projet si un ou plusieurs packages a été mis à jour. Parfois, un conflit de version se produit, ou une version de package a été dépréciée. Voici quelques conseils rapides pour vous aider à configurer votre fichier [package.json](https://docs.npmjs.com/files/package.json), et à comprendre ce qui se passe quand vous voyez des avertissements ou des erreurs. Il ne s’agit pas d’un guide complet sur *package.json* : seule la gestion des versions des packages npm est abordée.

Le système de gestion des versions des packages npm a des règles strictes. Le format des versions est celui-ci :

    [major].[minor].[patch]

Supposons que vous avez un package dans votre application avec une version 5.2.1. 5 correspond à la version principale, 2 à la version secondaire et 1 au correctif.

* Dans une mise à jour de la version principale, le package inclut de nouvelles fonctionnalités qui sont incompatibles avec la version précédente, c’est-à-dire des changements cassants.
* Dans une mise à jour de la version secondaire, les nouvelles fonctionnalités qui ont une compatibilité descendante avec les versions antérieures du package ont été ajoutées au package.
* Dans une mise à jour de correctif logiciel, un ou plusieurs correctifs de bogues sont inclus. Les correctifs de bogues ont toujours une compatibilité descendante.

Il est important de noter que certaines fonctionnalités des packages npm ont des dépendances. Par exemple, pour utiliser une nouvelle fonctionnalité du package du compilateur TypeScript (ts-loader) avec webpack, il est possible qu’une mise à jour des packages npm webpack et webpack-cli soit également nécessaire.

Pour faciliter la gestion les versions des packages, npm prend en charge plusieurs notations, que vous pouvez utiliser dans le fichier *package.json*. Vous pouvez utiliser ces notations pour contrôler le type des mises à jour de package que vous voulez accepter dans votre application.

Supposons que vous utilisez React et que vous devez inclure le package npm **react** et **react-dom**. Vous pouvez spécifier cela de plusieurs façons dans votre fichier *package.json*. Par exemple, vous pouvez spécifier l’utilisation de la version exacte d’un package comme suit.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Avec la notation précédente, npm obtiendra toujours la version exacte spécifiée, 16.4.2.

Vous pouvez utiliser une notation spéciale pour limiter les mises à jour aux mises à jour de correctifs logiciels (correctifs de bogues). Dans cet exemple :

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

vous utilisez le caractère tilde (~) pour indiquer à npm de mettre à jour un package seulement dans le cas de correctifs logiciels. Ainsi, npm peut mettre à jour react 16.4.2 vers 16.4.3 (ou 16.4.4, etc.), mais il n’accepte pas de mise à jour vers la version principale ou secondaire. 16.4.2 ne sera donc pas mis à jour vers 16.5.0.

Vous pouvez également utiliser le symbole d’insertion (^) pour spécifier que npm peut mettre à jour le numéro de version secondaire.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Avec cette notation, npm peut mettre à jour react 16.4.2 vers 16.5.0 (ou 16.5.1, 16.6.0, etc.), mais il n’accepte pas de mise à jour vers la version principale. 16.4.2 ne sera donc pas mis à jour vers 17.0.0.

Quand npm met à jour des packages, il génère un fichier *package-lock.json*, qui liste les versions des packages npm actuellement utilisées dans votre application, notamment les packages imbriqués. Si *package.json* gère les dépendances directes pour votre application, il ne gère cependant pas les dépendances imbriquées (les autres packages npm requis par un package npm particulier). Vous pouvez utiliser le fichier *package-lock.json* dans votre cycle de développement si vous devez vérifier que les autres développeurs et testeurs utilisent exactement les packages que vous utilisez vous-même, notamment les packages imbriqués. Pour plus d’informations, consultez [package-lock.json](https://docs.npmjs.com/files/package-lock.json) dans la documentation de npm.

Pour Visual Studio, le fichier *package-lock.json* n’est pas ajouté à votre projet, mais vous pouvez le trouver dans le dossier du projet.
