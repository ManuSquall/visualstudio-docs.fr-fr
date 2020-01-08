---
title: Afficher les éléments à importer
description: Utilisez afficher les éléments d’importation pour développer IntelliSense dans Visual Studio pour Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451509"
---
# <a name="show-import-items"></a>Afficher les éléments à importer

Visual Studio pour Mac pouvez afficher tous les types disponibles, même s’ils ne sont pas importés dans votre projet, dans votre liste de saisie semi-automatique IntelliSense. En sélectionnant un élément qui n’est pas importé, l’instruction `using` correcte sera ajoutée à votre fichier source.

![afficher la vue d’ensemble des éléments d’importation](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Comment activer

Pour activer cette fonctionnalité, ouvrez les **Préférences** par le biais de **Visual Studio** > **Préférences** et accédez à **éditeur de texte** > **IntelliSense**. Cochez la case **afficher les éléments à importer** pour activer des éléments supplémentaires dans IntelliSense.

![option Afficher les éléments à importer](media/show-import-items.png)

## <a name="usage"></a>Contrôle

Une fois que vous activez **afficher les éléments d’importation**, le processus d’utilisation de la fonctionnalité pour importer un élément est similaire aux actions normales dans IntelliSense. À mesure que vous tapez du code, les éléments valides remplissent la liste de saisie semi-automatique. Cela comprend les éléments qui n’ont pas encore été importés. Les éléments qui ne sont pas importés affichent leur espace de noms complet à droite de l’élément, ce qui vous permet de voir les importations que vous extrayez dans votre projet.

![afficher la liste des éléments à importer](media/show-import-items-list.png)

Dans la liste IntelliSense, les espaces de noms s’affichent en regard des membres qui ne sont pas actuellement référencés par une instruction `using`. Si vous choisissez l’un de ces éléments dans la liste, le membre est ajouté à votre code _et_ l’instruction `using` est ajoutée au début du fichier. Les membres des types déjà référencés dans le code codé n’afficheront pas leur espace de noms dans IntelliSense.

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)
