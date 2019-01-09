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
manager: wpickett
ms.prod: visual-studio-dev15
ms.workload:
- cplusplus
ms.openlocfilehash: c27673b8e6a5e0acce8f37fe20d675f56a62bbc6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846566"
---
# <a name="options-text-editor-cc-view"></a>Options, Éditeur de texte, C/C++, Affichage

Utilisez les pages de propriétés pour changer le comportement par défaut de l’Éditeur de code quand vous programmez en C ou C++.

Pour accéder à cette page de propriétés, choisissez **Outils** > **Options** et développez **Éditeur de texte**, puis **C/C++**, puis choisissez **Affichage**.

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
- [Refactorisation en C++ (blog VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
