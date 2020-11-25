---
title: Options, Éditeur de texte, C/C++, Affichage
description: Découvrez comment utiliser la page de vue dans la section C/C++ pour modifier le comportement par défaut des tildes de code, du code inactif, du mode plan et bien plus encore dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 68d08953ca3c493f3b3e42dd4ddd84bc19bdfd6e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041072"
---
# <a name="options-text-editor-cc-view"></a>Options, Éditeur de texte, C/C++, Affichage

Utilisez les pages de propriétés pour changer le comportement par défaut de l’Éditeur de code quand vous programmez en C ou C++.

Pour accéder à cette page de propriétés, choisissez **Outils**  >  **options** et développez **éditeur de texte**, puis **C/C++**, puis choisissez **Afficher**.

## <a name="code-squiggles"></a>Tildes dans le code

Vous pouvez activer ou désactiver les paramètres suivants pour gérer la façon dont l’éditeur de texte traite les tildes dans le code pour C et C++ :

- **Macros dans les régions ignorées par la navigation** : définit comment mettre en évidence les macros qui se trouvent dans des régions ignorées par la base de données de navigation, comme des macros dont les définitions incluent des accolades.

- **Macros convertibles en constexpr** : définit comment mettre en évidence les définitions de macro qui peuvent être converties en définitions `constexpr`.

## <a name="inactive-code"></a>Code inactif

- **Afficher les blocs inactifs** : les blocs inactifs du préprocesseur sont d’une autre couleur.

- **Désactiver l’opacité du code inactif** : une couleur unie est utilisée au lieu de l’opacité pour les blocs de code inactif.

- **Pourcentage d’opacité du code inactif** : pourcentage d’opacité des blocs de code inactif.

## <a name="miscellaneous"></a>Divers

- **Énumérer les tâches de commentaire** : recherche les jetons VS dans les fichiers sources ouverts et les affiche dans la fenêtre Liste des tâches.

- **Surligner les jetons correspondants** : surligne les accolades englobantes ou la syntaxe en correspondance où le curseur est positionné.

## <a name="outlining"></a>mode Plan

- **Activer le mode Plan** : passe en mode Plan quand un fichier s’ouvre.

- **Plan des régions Pragma** : passe automatiquement en mode Plan les blocs des régions `#pragma`.

- **Plan des blocs d’instruction** : passe automatiquement en mode Plan les blocs d’instructions.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’éditeur de Language-Specific](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorisation en C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
