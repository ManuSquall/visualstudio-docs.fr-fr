---
title: Options, Éditeur de texte, C/C++, Affichage
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: b867d81e4f0719ebf239bc89a6200fe833bc27b1
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919031"
---
# <a name="options-text-editor-cc-view"></a>Options, Éditeur de texte, C/C++, Affichage

Utilisez les pages de propriétés pour changer le comportement par défaut de l’Éditeur de code quand vous programmez en C ou C++.

Pour accéder à cette page de propriétés, choisissez **Outils** > **Options** et développez **Éditeur de texte**, puis **C/C++** , puis choisissez **Affichage**.

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

- [Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorisation en C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
