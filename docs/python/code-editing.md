---
title: Modification de code Python dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03effe56-d6f6-461d-9005-e43c15bf537c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: 0f2ecd6ca52a04e8813610c0f406251ef4604354
ms.lasthandoff: 04/10/2017

---

# <a name="editing-python-code"></a>Modification de code Python

La prise en charge de Python dans Visual Studio fournit plusieurs fonctionnalités conçues pour aider les développeurs à travailler plus rapidement dans l’éditeur de code, telles que la mise en surbrillance et la saisie semi-automatique de la syntaxe IntelliSense, l’assistance pour la signature, les substitutions de méthode, la recherche et la navigation. 

Dans cette rubrique :

- [IntelliSense](#intellisense), y compris les saisies semi-automatiques, l’assistance pour la signature, Info express et la coloration du code.
- [Extraits de code](#code-snippets)
- [Navigation dans votre code](#navigating-your-code)

Consultez [Écriture de code dans l’éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md) pour vous documenter sur la modification de code dans Visual Studio. Consultez également [Mode Plan](../ide/outlining.md), qui vous permet de rester concentré sur certaines sections de votre code. La prise en charge de Python inclut l’utilisation de l’Explorateur d’objets de Visual Studio (**Affichage > Autres fenêtres > Explorateur d’objets** ou Ctrl+W,J) pour l’inspection des classes définies dans chaque module et des fonctions définies dans ces classes. 

Pour obtenir une introduction à la modification de code Python, visionnez la vidéo [Getting Started with Python in Visual Studio, Part 3: Editing](https://youtu.be/uZGZNEyyeKs?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (Prise en main de Python dans Visual Studio, partie 3 : Modification ; youtube.com, 3 min48 s) :

> [!VIDEO https://www.youtube.com/embed/uZGZNEyyeKs]

## <a name="intellisense"></a>IntelliSense

IntelliSense fournit [les saisies semi-automatiques](#completions), [l’assistance pour la signature](#signature-help), [Info express](#quick-info) et [la coloration du code](#code-coloring). Pour améliorer le niveau de performance, IntelliSense dépend de la base de données de saisie semi-automatique qui est générée pour chaque environnement Python dans votre projet. Les bases de données doivent être actualisées si vous ajoutez, supprimez ou mettez à jour des packages. Leur état est affiché dans la fenêtre **Environnements Python** (de la même famille que l’Explorateur de solutions) de l’onglet **IntelliSense** (consultez [Environnements Python](python-environments.md)). 

### <a name="completions"></a>Saisies semi-automatiques

Les saisies semi-automatiques s’affichent sous forme d’instructions, d’identificateurs et d’autres mots qui peuvent tout à fait être saisis à l’emplacement actuel dans l’éditeur. Ce qui apparaît dans la liste est basé sur le contexte et est filtré pour omettre les options inappropriées ou inexactes. Les saisies semi-automatiques sont souvent déclenchées en tapant diverses instructions (comme `import`) et différents opérateurs (y compris un point), mais vous pouvez les afficher à tout moment en tapant la séquence suivante : Ctrl-J, espace.

![Saisie semi-automatique de membres](media/code-editing-completions-simple.png)

Lorsqu’une liste de saisies semi-automatiques est ouverte, vous pouvez rechercher la proposition que vous souhaitez grâce aux touches de direction, à la souris ou en continuant de taper. À mesure que vous tapez, la liste est filtrée pour afficher les propositions les plus probables. Ce filtrage intelligent vous permet d’utiliser des raccourcis tels que :

- Taper des lettres qui ne sont pas au début du nom, tel que « parse » pour rechercher « argparse ».
- Taper uniquement des lettres qui sont au début des mots, tel que « abc » pour rechercher « AbstractBaseClass » ou « air » pour rechercher « as_integer_ratio ».
- Ignorer des lettres, tel que « b64 » pour rechercher « base64 ».

Voici quelques exemples :

![Saisie semi-automatique de membres avec filtrage](media/code-editing-completion-filtering.png)

Les saisies semi-automatiques de membres apparaissent automatiquement lorsque vous tapez un point après une variable ou une valeur, et affichent les méthodes et les attributs des types potentiels. Si une variable peut être plus d’un type, la liste inclut toutes les possibilités de tous les types, avec des informations supplémentaires pour indiquer quels types prennent en charge chaque proposition. Lorsqu’une saisie semi-automatique est prise en charge par tous les types possibles, elle est affichée sans annotation.

![Saisie semi-automatique de membres sur plusieurs types](media/code-editing-completion-types.png)

Par défaut, les membres commençant et se terminant par un trait de soulignement double ne sont pas affichés. En règle générale, vous ne devez pas accéder à ces membres directement, mais si vous en avez besoin, taper le trait de soulignement double permettra d’ajouter ces saisies semi-automatiques à la liste :

![Saisie semi-automatique de membres privés](media/code-editing-completion-dunder.png)

Les instructions `import` et `from ... import` affichent une liste des modules qui peuvent être importés et, dans le cas de `from ... import`, les membres qui peuvent être importés à partir du module spécifié.

![Importation de saisie semi-automatique](media/code-editing-completion-import.png)

Les instructions `raise` et `except` affichent les listes des classes susceptibles d’être des types d’erreurs. Toutes les exceptions définies par l’utilisateur peuvent ne pas faire partie de ces listes, mais ces dernières vous permettront de trouver les exceptions intégrées appropriées rapidement :

![Saisie semi-automatique d’exceptions](media/code-editing-completion-exception.png)

Taper @ lance un décorateur et affiche les décorateurs potentiels. La plupart de ces éléments ne sont pas utilisables en tant que décorateurs et vous devez consulter la documentation de la bibliothèque pour déterminer lequel utiliser :

![Saisie semi-automatique de décorateurs](media/code-editing-completion-decorator.png)

> [!Tip]
> Vous pouvez configurer le comportement des saisies semi-automatiques via **Outils > Options > Éditeur de texte > Python > Avancé**. Parmi les options proposées, **Filter list based on search string** (Filtrer la liste en fonction de la chaîne de recherche) applique un filtre aux propositions de saisie semi-automatique à mesure que vous tapez (option sélectionnée par défaut) et **Member completion displays intersection of members** (La saisie semi-automatique de membres affiche l’intersection des membres) affiche uniquement les saisies semi-automatiques prises en charge par tous les types possibles (option non sélectionnée par défaut).


### <a name="signature-help"></a>Assistance pour la signature

Lorsque vous écrivez du code qui appelle une fonction, l’assistance pour la signature apparaît lorsque vous tapez le caractère `(` ouvrant et affiche les informations sur le paramètre et la documentation disponibles. Vous pouvez également les faire apparaître avec Ctrl + Maj + Espace à l’intérieur d’un appel de fonction. Les informations affichées dépendent des chaînes de documentation du code source de la fonction, mais elles incluent toutes les valeurs par défaut.

![Assistance pour la signature](media/code-editing-signature-help.png)

> [!Tip]
> Pour désactiver l’assistance pour la signature, accédez à **Outils > Options > Éditeur de texte > Python > Général** et désactivez **Saisie semi-automatique des instructions > Informations sur les paramètres**.

### <a name="quick-info"></a>Info express

Placer le pointeur de la souris sur un identificateur permet d’afficher une info-bulle Info express. En fonction de l’identificateur, Info express peut afficher les valeurs ou les types potentiels, la documentation disponible, les types de retour et les emplacements de définition :

![Info express](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Coloration du code

La coloration du code utilise les informations issues de l’analyse du code pour les variables de couleurs, les instructions et d’autres parties de votre code. Par exemple, les variables qui font référence à des modules ou à des classes peuvent être affichées dans une couleur différente pour des fonctions ou d’autres valeurs, et les noms de paramètres s’affichent dans une couleur différente pour les variables locales ou globales (notez que par défaut, les fonctions ne sont pas affichées en gras) :

![Coloration du code](media/code-editing-code-coloring.png)

Pour personnaliser les couleurs utilisées, accédez à **Outils > Options > Environnement > Polices et couleurs** et modifiez les entrées de Python dans la liste **Afficher les éléments**.

![Options Polices et couleurs](media/code-editing-customize-colors.png)

> [!Tip]
> Pour désactiver la coloration du code, accédez à **Outils > Options > Éditeur de texte > Python > Avancé** et désactivez **Options diverses > Color names based on type** (Colorer les noms en fonction du type).

## <a name="code-snippets"></a>Extraits de code

Les extraits de code sont des fragments de code qui peuvent être insérés dans vos fichiers en tapant un raccourci et en appuyant sur la touche de tabulation ou à l’aide des commandes **Modifier > IntelliSense > Insérer un extrait de code** **Entourer de**. Par exemple, si vous tapez `class` puis que vous appuyez sur la touche de tabulation, le reste de la classe est généré. Vous pouvez taper le nom et la liste de bases, passer d’un champ en surbrillance à l’autre avec la touche de tabulation, puis appuyer sur Entrée pour commencer à taper le corps du texte.

![Extraits de code](media/code-editing-code-snippets.png)

Vous pouvez voir les extraits de code disponibles dans le Gestionnaire des extraits de code (**Outils > Gestionnaire des extraits de code**), en sélectionnant **Python** comme langage :

![Gestionnaire des extraits de code](media/code-editing-code-snippets-manager.png)

Pour créer vos propres extraits de code, consultez [Procédure pas à pas : création d’un extrait de code](https://docs.microsoft.com/en-us/visualstudio/ide/walkthrough-creating-a-code-snippet).
Les extraits de code peuvent être personnalisés en [créant un extrait de code](https://msdn.microsoft.com/en-us/library/ms165394.aspx) et en l’important via 

Si vous écrivez un extrait de code de qualité et que vous souhaitez le partager, n’hésitez pas à le publier dans un contenu Gist et [informez-nous](https://github.com/Microsoft/PTVS/issues). Nous pourrons peut-être l’ajouter dans une prochaine version de Visual Studio.


## <a name="navigating-your-code"></a>Navigation dans votre code

La prise en charge de Python dans Visual Studio fournit plusieurs options pour naviguer rapidement dans votre code, notamment des bibliothèques pour lesquelles le code source est disponible : la [barre de navigation](#navigation-bar), [Atteindre la définition](#go-to-definition), [Naviguer vers](#navigate-to) et [Rechercher toutes les références](#find-all-references) (voir la description ci-dessous). Vous pouvez également utiliser l’[Explorateur d’objets](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) de Visual Studio.

### <a name="navigation-bar"></a>Barre de navigation

La barre de navigation s’affiche en haut de chaque fenêtre de l’éditeur et inclut une liste de définitions à deux niveaux. La liste déroulante de gauche contient des définitions de fonction et de classe de niveau supérieur du fichier actuel. La liste déroulante de droite affiche une liste de définitions dans l’étendue illustrée à gauche. À mesure de vos déplacements dans l’éditeur, ces listes sont mises à jour pour afficher votre contexte actuel. En outre, vous pouvez sélectionner une entrée à partir de ces listes pour atteindre directement celle-ci.

![Barre de navigation](media/code-editing-navigation-bar.png)

> [!Tip]
> Pour masquer la barre de navigation, accédez à **Outils > Options > Éditeur de texte > Python > Général** et désactivez **Paramètres > Barre de navigation**.

### <a name="go-to-definition"></a>Atteindre la définition

**Atteindre la définition** permet de passer rapidement de l’utilisation d’un identificateur (p. ex. un nom de fonction, une classe ou une variable) au code source dans lequel il est défini. Pour l’appeler, vous devez cliquer avec le bouton droit sur un identificateur et sélectionner **Atteindre la définition** ou placer le signe insertion dans l’identificateur et appuyer sur F12. Cela fonctionne dans l’ensemble de votre code et des bibliothèques externes sous réserve que ce code source soit disponible. Si le code source de la bibliothèque n’est pas disponible, **Atteindre la définition** passe à l’instruction `import` appropriée pour une référence de module ou affiche une erreur.

![Atteindre la définition](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Naviguer vers

La commande **Modifier > Naviguer vers...** (Ctrl-virgule) affiche une zone de recherche dans l’éditeur dans laquelle vous pouvez taper n’importe quelle chaîne et voir les correspondances possibles dans votre code qui définit une fonction, une classe ou une variable contenant cette chaîne. Cela permet de bénéficier d’une fonctionnalité similaire à **Atteindre la définition**, mais sans avoir à localiser une utilisation d’un identificateur.

Double-cliquer sur un nom ou sélectionner des touches de direction et Entrée permet d’accéder à la définition de cet identificateur.

![Naviguer vers](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Rechercher toutes les références

**Rechercher toutes les références** est une option utile pour déterminer où un identificateur donné est à la fois défini et utilisé, y compris les importations et les affectations. Pour l’appeler, vous devez cliquer avec le bouton droit sur un identificateur et sélectionner **Rechercher toutes les références** ou placer le signe insertion dans l’identificateur et appuyer sur Maj+F12. Double-cliquer sur un élément de la liste permet d’accéder à son emplacement.

![Résultats de Rechercher toutes les références](media/code-editing-find-all-references.png)
