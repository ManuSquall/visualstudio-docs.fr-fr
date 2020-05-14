---
title: Afficher les articles d’importation
description: Utilisez Show Import Items pour étendre IntelliSense dans Visual Studio pour Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451509"
---
# <a name="show-import-items"></a>Afficher les articles d’importation

Visual Studio pour Mac peut afficher tous les types disponibles, même s’ils ne sont pas importés à votre projet, dans votre liste d’achèvement IntelliSense. En sélectionnant un élément qui n’est `using` pas importé, la déclaration correcte sera ajoutée à votre fichier source.

![afficher l’aperçu des articles d’importation](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Comment activer

Pour activer cette fonctionnalité, ouvrez **Préférences** via **Visual Studio** > **Preferences** et naviguez vers **l’éditeur de** > texte**IntelliSense**. Cochez les **articles d’importation De la** case Afficher pour activer des articles supplémentaires dans IntelliSense.

![afficher l’option des articles d’importation](media/show-import-items.png)

## <a name="usage"></a>Usage

Une fois que vous **activez Afficher les articles d’importation**, le processus d’utilisation de la fonctionnalité pour importer un article est similaire aux actions normales au sein d’IntelliSense. Lorsque vous tapez du code, les éléments valides rempliront la liste d’achèvement. Cela comprend les articles qui n’ont pas encore été importés. Les articles qui ne sont pas importés montreront leur espace de nom complet à droite de l’article, vous permettant de voir quelles importations vous retirez dans votre projet.

![afficher la liste des articles d’importation](media/show-import-items-list.png)

Dans la liste IntelliSense, les espaces nominaux sont affichés à côté des membres qui ne sont pas actuellement référencés par une `using` déclaration. Si vous choisissez l’un de ces éléments de la liste, le membre sera ajouté à votre code _et_ l’instruction `using` sera ajoutée en haut du fichier. Les membres de types déjà référencés dans le code ne montreront pas leur namespace dans IntelliSense.

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)
