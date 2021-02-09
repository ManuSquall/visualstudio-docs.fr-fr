---
title: Modifier le code Python
description: Pour Python, Visual Studio fournit des fonctionnalités riches et diverses telles que la navigation, des extraits de code et IntelliSense, ainsi que la mise en forme, le linting et la refactorisation.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fa0caa8184f3c52a010df1dd1f82718d44be700b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888054"
---
# <a name="edit-python-code"></a>Modifier le code Python

Comme vous passez beaucoup de votre temps de développement dans l’éditeur de code, la [prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md) fournit plusieurs fonctionnalités pour améliorer la productivité. Ces fonctionnalités comprennent la mise en surbrillance de la syntaxe IntelliSense, la saisie semi-automatique, l’aide de signature, les substitutions de méthode, la recherche et la navigation.

L’éditeur est également intégré à la fenêtre **interactive** dans Visual Studio, ce qui facilite l’échange de code entre les deux. Pour plus d’informations, consultez [Étape 3 du tutoriel : Utiliser la fenêtre REPL interactive](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) et [Utiliser la fenêtre interactive - Commande Envoyer vers Interactive](python-interactive-repl-in-visual-studio.md#send-to-interactive-command).

Pour vous documenter sur la modification de code dans Visual Studio, consultez [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md). Consultez également [Mode Plan](../ide/outlining.md), qui vous permet de rester concentré sur certaines sections de votre code.

Vous pouvez également utiliser **l’Explorateur d’objets** de Visual Studio (**Affichage** > **Autres fenêtres** > **Explorateur d’objets** ou **Ctrl**+**W** > **J**) pour l’inspection des classes Python définies dans chaque module et les fonctions définies dans ces classes.

## <a name="intellisense"></a>IntelliSense

IntelliSense fournit [les saisies semi-automatiques](#completions), [l’assistance pour la signature](#signature-help), [Info express](#quick-info) et [la coloration du code](#code-coloring). Visual Studio 2017 version 15.7 et les versions ultérieures prennent également en charge les [affinages de type](#type-hints).

Pour améliorer les performances, IntelliSense dans Visual Studio 2017 version 15.5 et antérieure dépend d’une base de données de complétion qui est générée pour chaque environnement Python dans votre projet. Il est possible que les bases de données doivent être actualisées si vous ajoutez, supprimez ou mettez à jour des packages. Leur état s’affiche sous l’onglet **IntelliSense** de la fenêtre **Environnements Python** (de la même famille que **l’Explorateur de solutions**) (consultez [Référence sur la fenêtre Environnements](python-environments-window-tab-reference.md)).

Visual Studio 2017 version 15.6 et ultérieure utilise un autre moyen pour fournir des complétions IntelliSense qui ne dépendent pas de la base de données.

### <a name="completions"></a>Saisies semi-automatiques

Les saisies semi-automatiques s’affichent sous forme d’instructions, d’identificateurs et d’autres mots qui peuvent tout à fait être saisis à l’emplacement actuel dans l’éditeur. Ce qui apparaît dans la liste est basé sur le contexte et est filtré pour omettre les options inappropriées ou inexactes. Les saisies semi-automatiques sont souvent déclenchées en tapant des instructions différentes (telles que `import` ) et des opérateurs (y compris un point), mais vous pouvez les afficher à tout moment en tapant **CTRL** + **J**  >  **Space**.

![Saisie semi-automatique de membres dans l’éditeur Visual Studio](media/code-editing-completions-simple.png)

Lorsqu’une liste de saisies semi-automatiques est ouverte, vous pouvez rechercher la proposition que vous souhaitez grâce aux touches de direction, à la souris ou en continuant de taper. À mesure que vous tapez, la liste est filtrée pour afficher les propositions les plus probables. Vous pouvez également utiliser des raccourcis tels que :

- Taper des lettres qui ne sont pas au début du nom, tel que « parse » pour rechercher « argparse ».
- Taper uniquement des lettres qui sont au début des mots, tel que « abc » pour rechercher « AbstractBaseClass » ou « air » pour rechercher « as_integer_ratio ».
- Ignorer des lettres, tel que « b64 » pour rechercher « base64 ».

Exemples :

![Saisie semi-automatique de membres avec filtrage dans l’éditeur Visual Studio](media/code-editing-completion-filtering.png)

Les saisies semi-automatiques de membres apparaissent automatiquement quand vous tapez un point après une variable ou une valeur, ainsi que les méthodes et attributs des types potentiels. Si une variable peut être plus d’un type, la liste inclut toutes les possibilités de tous les types, avec des informations supplémentaires pour indiquer quels types prennent en charge chaque proposition. Lorsqu’une saisie semi-automatique est prise en charge par tous les types possibles, elle est affichée sans annotation.

![Saisie semi-automatique de membres sur plusieurs types dans l’éditeur Visual Studio](media/code-editing-completion-types.png)

Par défaut, les membres commençant et se terminant par un trait de soulignement double ne sont pas affichés. En règle générale, vous ne devez pas accéder à ces membres directement. Toutefois, si vous en avez besoin, la saisie du trait de soulignement double de début permet d’ajouter ces saisies semi-automatiques à la liste :

![Saisie semi-automatique de membres privés dans l’éditeur Visual Studio](media/code-editing-completion-dunder.png)

Les instructions `import` et `from ... import` affichent une liste des modules qui peuvent être importés. Dans le cas de `from ... import`, la liste inclut les membres qui peuvent être importés à partir du module spécifié.

![Importation de saisie semi-automatique dans l’éditeur Visual Studio](media/code-editing-completion-import.png)

Les instructions `raise` et `except` affichent les listes des classes susceptibles d’être des types d’erreurs. Les exceptions définies par l’utilisateur peuvent ne pas toutes faire partie de cette liste, mais elle vous permet de trouver les exceptions intégrées appropriées rapidement :

![Saisie semi-automatique d’exceptions dans l’éditeur Visual Studio](media/code-editing-completion-exception.png)

Taper @ lance un décorateur et affiche les décorateurs potentiels. La plupart de ces éléments ne sont pas utilisables en tant que décorateurs ; consultez la documentation de la bibliothèque pour déterminer lequel utiliser.

![Saisie semi-automatique de décorateurs dans l’éditeur Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Vous pouvez configurer le comportement des saisies semi-automatiques à l’aide des **Outils**  >  **options**  >  **éditeur de texte**  >  **python**  >  **avancé**. Parmi celles-ci, la **liste de filtres basée sur la chaîne de recherche applique le** filtrage des suggestions de saisie semi-automatique au fur et à mesure que vous tapez (activé par défaut), et la **saisie semi** -automatique des membres affiche les saisies semi-automatiques qui sont prises en charge par tous les types possibles (la valeur par défaut est désactivée). Consultez [Options - Résultats de la saisie semi-automatique](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Affinages de type

*Visual Studio 2017 version 15,7 et versions ultérieures.*

Les « affinages de type » dans Python 3.5+ ([PEP 484](https://www.python.org/dev/peps/pep-0484/), python.org) font référence à une syntaxe d’annotation pour les fonctions et classes qui indiquent les types des arguments, des valeurs de retour et des attributs de classe. IntelliSense affiche des affinages de type quand vous pointez sur des appels de fonctions, des arguments et des variables dotés de ces annotations.

Dans l’exemple ci-dessous, la classe `Vector` est déclarée en tant que `List[float]` et la fonction `scale` contient les affinages de type de ses arguments et de sa valeur de retour. Quand vous pointez sur un appel à cette fonction, les affinages de type apparaissent :

![Pointage sur un appel de fonction pour afficher les affinages de type](media/code-editing-type-hints1.png)

Dans l’exemple suivant, vous pouvez voir comment les attributs annotés de la classe `Employee` apparaissent dans la fenêtre contextuelle de complétion IntelliSense associée à un attribut :

![Complétion IntelliSense illustrant les affinages de type](media/code-editing-type-hints2.png)

De plus, il s’avère utile de valider les affinages de type tout au long de votre projet, car ce n’est normalement qu’au moment de l’exécution que les erreurs apparaissent. À cet effet, Visual Studio intègre l’outil MyPy (Industry Standard) à l’aide de la commande de menu contextuel de **python**  >  **Run MyPy** dans **Explorateur de solutions**:

![Exécuter la commande de menu contextuel MyPy dans l’Explorateur de solutions](media/code-editing-type-hints-run-mypy.png)

Quand vous exécutez la commande, vous êtes invité à installer le package mypy, si nécessaire. Visual Studio exécute ensuite mypy pour valider les affinages de type dans chaque fichier Python du projet. Les erreurs apparaissent dans la fenêtre Visual Studio **Liste d’erreurs**. Quand vous sélectionnez un élément dans la fenêtre, vous accédez à la ligne appropriée dans votre code.

À titre de simple exemple, la définition de fonction suivante contient un affinage de type pour signaler que l’argument `input` est de type `str`, alors que l’appel à cette fonction tente de passer un entier :

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

L’utilisation de la commande **Exécuter Mypy** sur ce code génère l’erreur suivante :

![Exemple de résultat de la validation des affinages de type par mypy](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Pour les versions de Python antérieures à la version 3.5, Visual Studio affiche également les affinages de type que vous fournissez par le biais de *fichiers stub* Typeshed (*.pyi*). Vous pouvez utiliser des fichiers stub chaque fois que vous ne souhaitez pas inclure d’indicateurs de type directement dans votre code, ou que vous souhaitez créer des affinages de type pour une bibliothèque qui ne les utilise pas directement. Pour plus d’informations, consultez [créer des stubs pour les modules python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) dans le wiki de projet mypy.
>
> Visual Studio ne prend pas en charge les affinages de type dans les commentaires.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Pour les versions de Python antérieures à la version 3.5, Visual Studio affiche également les affinages de type que vous fournissez par le biais de *fichiers stub* Typeshed (*.pyi*). Vous pouvez utiliser des fichiers stub chaque fois que vous ne souhaitez pas inclure d’indicateurs de type directement dans votre code, ou que vous souhaitez créer des affinages de type pour une bibliothèque qui ne les utilise pas directement. Pour plus d’informations, consultez [créer des stubs pour les modules python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) dans le wiki de projet mypy.
>
> Visual Studio inclut un ensemble de groupes de fichiers Typeshed pour Python 2 et 3, des téléchargements supplémentaires ne sont donc pas nécessaires. Toutefois, si vous souhaitez utiliser un autre ensemble de fichiers, vous pouvez spécifier le chemin d’accès dans les options des **Outils** options du  >    >  serveur de  >  **langage** Python. Consultez [Options - Serveur de langage](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Visual Studio ne prend pas en charge les affinages de type dans les commentaires.
::: moniker-end

### <a name="signature-help"></a>Assistance pour la signature

Quand vous écrivez du code qui appelle une fonction, l’aide de signature apparaît lorsque vous tapez le caractère `(` ouvrant et affiche les informations sur le paramètre et la documentation disponibles. Vous pouvez également l’afficher avec **CTRL** + **+** + **espace** dans un appel de fonction. Les informations affichées dépendent des chaînes de documentation du code source de la fonction, mais elles incluent toutes les valeurs par défaut.

![Assistance pour la signature dans l’éditeur Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Pour désactiver l’aide sur les signatures, accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **python**  >  **général** et effacez les informations sur les paramètres de **saisie semi-automatique des instructions**  >  .

### <a name="quick-info"></a>Info express

Placer le pointeur de la souris sur un identificateur permet d’afficher une info-bulle Info express. En fonction de l’identificateur, Info express peut afficher les valeurs ou les types potentiels, la documentation disponible, les types de retour et les emplacements de définition :

![Informations rapides dans l’éditeur Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Coloration du code

La coloration du code utilise les informations issues de l’analyse du code pour les variables de couleurs, les instructions et d’autres parties de votre code. Par exemple, les variables qui font référence à des modules ou à des classes peuvent être affichées dans une couleur différente des fonctions ou d’autres valeurs, et les noms de paramètres s’affichent dans une couleur différente des variables locales ou globales. (Par défaut, les fonctions ne sont pas affichées en gras) :

![Coloration du code et de la syntaxe dans l’éditeur Visual Studio](media/code-editing-code-coloring.png)

Pour personnaliser les couleurs, accédez à **Outils**  >  **options**  >  **environnement**  >  **polices et couleurs** et modifiez les entrées **python** dans la liste **éléments affichés** :

![Options Polices et Couleurs dans Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Pour désactiver la coloration du code, accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **python**  >  **avancé** et désélectionnez **divers options**  >  **noms de couleurs basés sur le type**. Consultez [options-options diverses](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Extraits de code

Les extraits de code sont des fragments de code qui peuvent être insérés dans vos fichiers en tapant un raccourci et en appuyant sur **Tab** ou à l’aide des commandes **Modifier** > **IntelliSense** > **Insérer un extrait de code** et **Entourer de**, en sélectionnant **Python**, puis l’extrait de code requis.

Par exemple, `class` est un raccourci pour un extrait de code qui insère une définition de classe. L’extrait de code s’affiche dans la liste de saisie semi-automatique lorsque vous tapez `class` :

![Raccourci d’extrait de code pour la classe](media/code-editing-code-snippet-class.png)

Appuyez sur **Tab** pour générer le reste de la classe. Vous pouvez ensuite taper le nom et la liste de bases, passer d’un champ en surbrillance à l’autre avec la touche **Tab**, puis appuyer sur **Entrée** pour commencer à taper le corps du texte.

![Mise en évidence des zones d’un extrait de code que vous devez remplir](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Commandes de menu

Quand vous utilisez la   >  commande de menu modifier l’extrait de code d’insertion **IntelliSense**  >  , vous sélectionnez d’abord **python**, puis vous sélectionnez un extrait de **code** :

![Sélection d’un extrait de code via la commande Insérer un extrait de code](media/code-editing-code-snippet-insert.png)

La commande **modifier** l'  >    >  **Entourage IntelliSense avec** , de la même façon, place la sélection actuelle dans l’éditeur de texte à l’intérieur d’un élément structurel choisi. Par exemple, supposons que vous ayez un peu de code comme suit :

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Le fait de sélectionner ce code et de choisir la commande **Entourer de** affiche la liste des extraits de code disponibles. Le fait de choisir **def** dans la liste place le code sélectionné au sein d’une définition de fonction et vous pouvez utiliser la touche **Tab** pour naviguer entre le nom et les arguments de la fonction sélectionnée :

![Utilisation de la commande Entourer de pour les extraits de code](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Examiner les extraits de code disponibles

Vous pouvez voir les extraits de code disponibles dans le **Gestionnaire des extraits de code**, que vous ouvrez avec la commande de menu **Outils** > **Gestionnaire des extraits de code** et en sélectionnant **Python** comme langage :

![Gestionnaire des extraits de code dans Visual Studio](media/code-editing-code-snippets-manager.png)

Pour créer vos propres extraits de code, consultez [Procédure pas à pas : créer un extrait de code](../ide/walkthrough-creating-a-code-snippet.md).

Si vous écrivez un extrait de code de qualité et que vous souhaitez le partager, n’hésitez pas à le publier dans un contenu Gist et [informez-nous](https://github.com/Microsoft/PTVS/issues). Nous pourrons peut-être l’ajouter dans une prochaine version de Visual Studio.

## <a name="navigate-your-code"></a>Parcourir votre code

La prise en charge de Python dans Visual Studio fournit plusieurs moyens de naviguer rapidement dans votre code, y compris les bibliothèques pour lesquelles le code source est disponible : la [barre de navigation](#navigation-bar), [**atteindre la définition**](#go-to-definition), [**accéder à**](#navigate-to)et [**Rechercher toutes les références**](#find-all-references). Vous pouvez également utiliser l' [**Explorateur d’objets**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)de Visual Studio.

### <a name="navigation-bar"></a>Barre de navigation

La barre de navigation s’affiche en haut de chaque fenêtre de l’éditeur et inclut une liste de définitions à deux niveaux. La liste déroulante de gauche contient des définitions de fonction et de classe de niveau supérieur du fichier actuel. La liste déroulante de droite affiche une liste de définitions dans l’étendue illustrée à gauche. À mesure de vos déplacements dans l’éditeur, les listes sont mises à jour pour afficher votre contexte actuel. En outre, vous pouvez sélectionner une entrée à partir de ces listes pour y accéder directement.

![Barre de navigation dans l’éditeur Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Pour masquer la barre de navigation, accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **python**  >  **général** et désactivez la barre de   >  **navigation** paramètres.

### <a name="go-to-definition"></a>Atteindre la définition

**Atteindre la définition** permet de passer rapidement de l’utilisation d’un identificateur (p. ex. un nom de fonction, une classe ou une variable) au code source dans lequel il est défini. Pour l’appeler, vous devez cliquer avec le bouton droit sur un identificateur et sélectionner **atteindre la définition** ou placer le signe insertion dans l’identificateur et appuyer sur **F12**. Cela fonctionne dans l’ensemble de votre code et des bibliothèques externes sous réserve que ce code source soit disponible. Si le code source de la bibliothèque n’est pas disponible, **Atteindre la définition** passe à l’instruction `import` appropriée pour une référence de module ou affiche une erreur.

![Commande Atteindre la définition dans Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Naviguer vers

La commande **modifier**  >  **naviguer vers** (**CTRL** + **,**) affiche une zone de recherche dans l’éditeur dans laquelle vous pouvez taper n’importe quelle chaîne et voir les correspondances possibles dans votre code qui définit une fonction, une classe ou une variable contenant cette chaîne. Cette fonctionnalité permet de bénéficier d’une fonction similaire à **Atteindre la définition**, mais sans avoir à localiser une utilisation d’un identificateur.

Double-cliquez sur un nom, ou sélectionnez avec les touches de direction et **entrée** pour accéder à la définition de cet identificateur.

![Commande Naviguer vers dans Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Rechercher toutes les références

**Rechercher toutes les références** est une option utile pour déterminer où un identificateur donné est à la fois défini et utilisé, y compris les importations et les affectations. Vous l’appelez en cliquant avec le bouton droit sur un identificateur et en sélectionnant **Rechercher toutes les références**, ou en plaçant le signe insertion dans l’identificateur et en appuyant sur **MAJ** + **F12**. Double-cliquer sur un élément de la liste permet d’accéder à son emplacement.

![Résultats de Rechercher toutes les références](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Voir aussi

- [Mise en forme](formatting-python-code.md)
- [Refactorisation](refactoring-python-code.md)
- [Utiliser un linter](linting-python-code.md)
