---
title: Modification de code Python dans Visual Studio | Microsoft Docs
description: "La modification de Python dans Visual Studio fournit des fonctionnalités diverses telles que la navigation, des extraits de code et IntelliSense, ainsi que la mise en forme, le linting et la refactorisation."
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: e2bbf7169e7d60d5dac1119f543cbcfe61e922ff
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="editing-python-code"></a>Modification de code Python

Comme les développeurs passent beaucoup de temps dans l’éditeur de code, la [prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md) fournit plusieurs fonctionnalités pour améliorer la productivité. Ces fonctionnalités comprennent la mise en surbrillance de la syntaxe IntelliSense, la saisie semi-automatique, l’aide de signature, les substitutions de méthode, la recherche et la navigation. 

L’éditeur est également intégré à la fenêtre interactive dans Visual Studio, ce qui facilite l’échange de code entre les deux. Pour plus d’informations, consultez [Étape 3 du didacticiel : Utilisation de la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) et [Utilisation de la fenêtre REPL interactive - Envoi de code à la commande interactive](python-interactive-repl-in-visual-studio.md#send-code-to-interactive-command).

Pour une introduction à l’édition de code Python, consultez [Editing Python Code](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567) (Microsoft Virtual Academy, 2 minutes 30 secondes) :

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567]

Consultez [Écriture de code dans l’éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md) pour vous documenter sur la modification de code dans Visual Studio. Consultez également [Mode Plan](../ide/outlining.md), qui vous permet de rester concentré sur certaines sections de votre code.

Vous pouvez également utiliser l’Explorateur d’objets de Visual Studio (**Affichage > Autres fenêtres > Explorateur d’objets** ou Ctrl+W, J) pour l’inspection des classes Python définies dans chaque module et les fonctions définies dans ces classes.

## <a name="intellisense"></a>IntelliSense

IntelliSense fournit [les saisies semi-automatiques](#completions), [l’assistance pour la signature](#signature-help), [Info express](#quick-info) et [la coloration du code](#code-coloring). Pour améliorer le niveau de performance, IntelliSense dépend de la base de données de saisie semi-automatique qui est générée pour chaque environnement Python dans votre projet. Il est possible que les bases de données doivent être actualisées si vous ajoutez, supprimez ou mettez à jour des packages. Leur état est affiché dans la fenêtre **Environnements Python** (de la même famille que l’Explorateur de solutions) de l’onglet **IntelliSense** (consultez [Environnements Python](managing-python-environments-in-visual-studio.md)). 

### <a name="completions"></a>Saisies semi-automatiques

Les saisies semi-automatiques s’affichent sous forme d’instructions, d’identificateurs et d’autres mots qui peuvent tout à fait être saisis à l’emplacement actuel dans l’éditeur. Ce qui apparaît dans la liste est basé sur le contexte et est filtré pour omettre les options inappropriées ou inexactes. Les saisies semi-automatiques sont souvent déclenchées en tapant diverses instructions (comme `import`) et différents opérateurs (dont un point), mais vous pouvez les afficher à tout moment en tapant la séquence suivante : Ctrl+J, espace.

![Saisie semi-automatique de membres](media/code-editing-completions-simple.png)

Lorsqu’une liste de saisies semi-automatiques est ouverte, vous pouvez rechercher la proposition que vous souhaitez grâce aux touches de direction, à la souris ou en continuant de taper. À mesure que vous tapez, la liste est filtrée pour afficher les propositions les plus probables. Vous pouvez également utiliser des raccourcis tels que :

- Taper des lettres qui ne sont pas au début du nom, tel que « parse » pour rechercher « argparse ».
- Taper uniquement des lettres qui sont au début des mots, tel que « abc » pour rechercher « AbstractBaseClass » ou « air » pour rechercher « as_integer_ratio ».
- Ignorer des lettres, tel que « b64 » pour rechercher « base64 ».

Voici quelques exemples :

![Saisie semi-automatique de membres avec filtrage](media/code-editing-completion-filtering.png)

Les saisies semi-automatiques de membres apparaissent automatiquement quand vous tapez un point après une variable ou une valeur, ainsi que les méthodes et attributs des types potentiels. Si une variable peut être plus d’un type, la liste inclut toutes les possibilités de tous les types, avec des informations supplémentaires pour indiquer quels types prennent en charge chaque proposition. Lorsqu’une saisie semi-automatique est prise en charge par tous les types possibles, elle est affichée sans annotation.

![Saisie semi-automatique de membres sur plusieurs types](media/code-editing-completion-types.png)

Par défaut, les membres commençant et se terminant par un trait de soulignement double ne sont pas affichés. En règle générale, vous ne devez pas accéder à ces membres directement. Toutefois, si vous en avez besoin, la saisie du trait de soulignement double de début permet d’ajouter ces saisies semi-automatiques à la liste :

![Saisie semi-automatique de membres privés](media/code-editing-completion-dunder.png)

Les instructions `import` et `from ... import` affichent une liste des modules qui peuvent être importés. Dans le cas de `from ... import`, la liste inclut les membres qui peuvent être importés à partir du module spécifié.

![Importation de saisie semi-automatique](media/code-editing-completion-import.png)

Les instructions `raise` et `except` affichent les listes des classes susceptibles d’être des types d’erreurs. Les exceptions définies par l’utilisateur peuvent ne pas toutes faire partie de cette liste, mais elle vous permet de trouver les exceptions intégrées appropriées rapidement :

![Saisie semi-automatique d’exceptions](media/code-editing-completion-exception.png)

Taper @ lance un décorateur et affiche les décorateurs potentiels. La plupart de ces éléments ne sont pas utilisables en tant que décorateurs ; consultez la documentation de la bibliothèque pour déterminer lequel utiliser.

![Saisie semi-automatique de décorateurs](media/code-editing-completion-decorator.png)

> [!Tip]
> Vous pouvez configurer le comportement des saisies semi-automatiques via **Outils > Options > Éditeur de texte > Python > Avancé**. Parmi les options proposées, **Filter list based on search string** (Filtrer la liste en fonction de la chaîne de recherche) applique un filtre aux propositions de saisie semi-automatique à mesure que vous tapez (option sélectionnée par défaut) et **Member completion displays intersection of members** (La saisie semi-automatique de membres affiche l’intersection des membres) affiche uniquement les saisies semi-automatiques prises en charge par tous les types possibles (option non sélectionnée par défaut). Consultez [Options - Résultats de la saisie semi-automatique](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="signature-help"></a>Assistance pour la signature

Quand vous écrivez du code qui appelle une fonction, l’aide de signature apparaît lorsque vous tapez le caractère `(` ouvrant et affiche les informations sur le paramètre et la documentation disponibles. Vous pouvez également les faire apparaître avec Ctrl + Maj + Espace à l’intérieur d’un appel de fonction. Les informations affichées dépendent des chaînes de documentation du code source de la fonction, mais elles incluent toutes les valeurs par défaut.

![Assistance pour la signature](media/code-editing-signature-help.png)

> [!Tip]
> Pour désactiver l’assistance pour la signature, accédez à **Outils > Options > Éditeur de texte > Python > Général** et désactivez **Saisie semi-automatique des instructions > Informations sur les paramètres**.

### <a name="quick-info"></a>Info express

Placer le pointeur de la souris sur un identificateur permet d’afficher une info-bulle Info express. En fonction de l’identificateur, Info express peut afficher les valeurs ou les types potentiels, la documentation disponible, les types de retour et les emplacements de définition :

![Info express](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Coloration du code

La coloration du code utilise les informations issues de l’analyse du code pour les variables de couleurs, les instructions et d’autres parties de votre code. Par exemple, les variables qui font référence à des modules ou à des classes peuvent être affichées dans une couleur différente des fonctions ou d’autres valeurs, et les noms de paramètres s’affichent dans une couleur différente des variables locales ou globales. (Par défaut, les fonctions ne sont pas affichées en gras) :

![Coloration du code](media/code-editing-code-coloring.png)

Pour personnaliser les couleurs, accédez à **Outils > Options > Environnement > Polices et couleurs** et modifiez les entrées de Python dans la liste **Afficher les éléments** :

![Options Polices et couleurs](media/code-editing-customize-colors.png)

> [!Tip]
> Pour désactiver la coloration du code, accédez à **Outils > Options > Éditeur de texte > Python > Avancé** et désactivez **Options diverses > Color names based on type** (Colorer les noms en fonction du type). Consultez [Options - Options diverses](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Extraits de code

Les extraits de code sont des fragments de code qui peuvent être insérés dans vos fichiers en tapant un raccourci et en appuyant sur la touche de tabulation ou à l’aide des commandes **Modifier > IntelliSense > Insérer un extrait de code** **Entourer de**. Par exemple, si vous tapez `class` et appuyez sur la touche Tab, le reste de la classe est généré. Vous pouvez taper le nom et la liste de bases, passer d’un champ en surbrillance à l’autre avec la touche de tabulation, puis appuyer sur Entrée pour commencer à taper le corps du texte.

![Extraits de code](media/code-editing-code-snippets.png)

Vous pouvez voir les extraits de code disponibles dans le Gestionnaire des extraits de code (**Outils > Gestionnaire des extraits de code**), en sélectionnant **Python** comme langage :

![Gestionnaire des extraits de code](media/code-editing-code-snippets-manager.png)

Pour créer vos propres extraits de code, consultez [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md). 

Si vous écrivez un extrait de code de qualité et que vous souhaitez le partager, n’hésitez pas à le publier dans un contenu Gist et [informez-nous](https://github.com/Microsoft/PTVS/issues). Nous pourrons peut-être l’ajouter dans une prochaine version de Visual Studio.

## <a name="navigating-your-code"></a>Navigation dans votre code

La prise en charge de Python dans Visual Studio fournit plusieurs options pour naviguer rapidement dans votre code, notamment des bibliothèques pour lesquelles le code source est disponible : la [barre de navigation](#navigation-bar), [Atteindre la définition](#go-to-definition), [Naviguer vers](#navigate-to) et [Rechercher toutes les références](#find-all-references). Vous pouvez également utiliser l’[Explorateur d’objets](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) de Visual Studio.

### <a name="navigation-bar"></a>Barre de navigation

La barre de navigation s’affiche en haut de chaque fenêtre de l’éditeur et inclut une liste de définitions à deux niveaux. La liste déroulante de gauche contient des définitions de fonction et de classe de niveau supérieur du fichier actuel. La liste déroulante de droite affiche une liste de définitions dans l’étendue illustrée à gauche. À mesure de vos déplacements dans l’éditeur, les listes sont mises à jour pour afficher votre contexte actuel. En outre, vous pouvez sélectionner une entrée à partir de ces listes pour y accéder directement.

![Barre de navigation](media/code-editing-navigation-bar.png)

> [!Tip]
> Pour masquer la barre de navigation, accédez à **Outils > Options > Éditeur de texte > Python > Général** et désactivez **Paramètres > Barre de navigation**.

### <a name="go-to-definition"></a>Atteindre la définition

**Atteindre la définition** permet de passer rapidement de l’utilisation d’un identificateur (p. ex. un nom de fonction, une classe ou une variable) au code source dans lequel il est défini. Pour l’appeler, vous devez cliquer avec le bouton droit sur un identificateur et sélectionner **Atteindre la définition** ou placer le signe insertion dans l’identificateur et appuyer sur F12. Cela fonctionne dans l’ensemble de votre code et des bibliothèques externes sous réserve que ce code source soit disponible. Si le code source de la bibliothèque n’est pas disponible, **Atteindre la définition** passe à l’instruction `import` appropriée pour une référence de module ou affiche une erreur.

![Atteindre la définition](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Boîte de dialogue Naviguer vers

La commande **Modifier > Naviguer vers...** (Ctrl-virgule) affiche une zone de recherche dans l’éditeur dans laquelle vous pouvez taper n’importe quelle chaîne et voir les correspondances possibles dans votre code qui définit une fonction, une classe ou une variable contenant cette chaîne. Cette fonctionnalité permet de bénéficier d’une fonction similaire à **Atteindre la définition**, mais sans avoir à localiser une utilisation d’un identificateur.

Double-cliquer sur un nom ou sélectionner des touches de direction et Entrée permet d’accéder à la définition de cet identificateur.

![Boîte de dialogue Naviguer vers](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Rechercher toutes les références

**Rechercher toutes les références** est une option utile pour déterminer où un identificateur donné est à la fois défini et utilisé, y compris les importations et les affectations. Pour l’appeler, vous devez cliquer avec le bouton droit sur un identificateur et sélectionner **Rechercher toutes les références** ou placer le signe insertion dans l’identificateur et appuyer sur Maj+F12. Double-cliquer sur un élément de la liste permet d’accéder à son emplacement.

![Résultats de Rechercher toutes les références](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Voir aussi

- [Mise en forme](formatting-python-code.md)
- [Refactorisation](refactoring-python-code.md)
- [Linting](linting-python-code.md)