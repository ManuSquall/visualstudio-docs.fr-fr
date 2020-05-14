---
title: Extraits de code
description: Comment utiliser des extraits de code pour programmer efficacement dans Visual Studio pour Mac
author: cobey
ms.author: cobey
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 1dacc935549d738ff1b5e84c3ac4420c343155fd
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68787698"
---
# <a name="code-snippets"></a>Extraits de code

Les extraits de code, souvent appelés _modèles de code_, sont pratiques pour une programmation efficace, car ils permettent l’insertion et la modification de blocs de code pré-écrits. L’utilisation d’extraits de code peut être pratique pour ajouter rapidement des modèles courants, ou même pour apprendre de nouveaux modèles quand vous, en tant que développeur, n’êtes pas sûr de la syntaxe. Des modèles sont fournis pour C#, F#, HTML, XML, Python et Razor.

Cette section explique comment créer, insérer et utiliser des extraits dans du code.

## <a name="inserting-a-snippet"></a>Insertion d’un extrait de code

Il existe différentes façons d’ajouter des extraits de code, dont certaines sont décrites ci-dessous :

- **Tabulation : ** &ndash; commencez à taper le nom du modèle, sélectionnez-le dans la liste, puis appuyez sur **Tab**, **Tab** pour l’ajouter :

  ![Expansion de tabulation dans du code](media/source-editor-image13.png)

- **Boîte à outils : ** &ndash; utilisez le panneau Boîte à outils pour afficher une liste de tous les extraits de code. Faites glisser n’importe quel modèle depuis la boîte à outils à la position correcte dans le code source :

  [![Extraits de code dans la boîte à outils](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Commande Insérer des modèles : ** &ndash; il n’existe actuellement pas de combinaison de touches par défaut définie pour l’insertion d’un modèle. Pour en créer une, accédez à **Visual Studio > Préférences > Combinaison de touches**, puis recherchez `template`. Ceci permet d’ajouter la combinaison de touches souhaitée dans le champ Modifier la combinaison. Cliquez ensuite sur **Appliquer** :

  ![Commande Insérer un modèle](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Création d’un modèle

Il existe de nombreux modèles dans différents langages que vous pouvez utiliser et modifier, mais vous pouvez aussi ajouter de nouveaux modèles en accédant à **Visual Studio > Préférences > Éditeur de texte > Extraits de code**:

![Insérer un nouveau modèle](media/source-editor-image12.png)

Appuyez sur le bouton **Ajouter** ou **Modifier** pour créer ou modifier des extraits de code.

## <a name="keywords-in-code-snippets"></a>Mots clés dans les extraits de code

Une fois qu’un extrait de code est inséré dans l’éditeur, tous les mots clés définis sont mis en surbrillance et peuvent être modifiés en utilisant la tabulation pour naviguer entre eux. Les mots clés se comportent comme une « variable » dans l’extrait de code et sont définis en plaçant un signe dollar `$` avant et après le nom du mot clé. 

La fenêtre **Modifier un modèle** est illustrée ci-dessous, avec la modification de l’extrait de code `prop` intégré. L’extrait contient deux mots &ndash; `$type$` `$name$` &ndash; clés et qui peuvent avoir d’autres propriétés définies (comme une valeur par défaut et une pointe d’outils) sur le côté droit de la fenêtre :

![Fenêtre Modifier un modèle](media/source-editor-image12z.png)

Les champs suivants sont utilisés pour définir un extrait de code :

- **Raccourci** &ndash; Le texte entré par l’utilisateur pour insérer l’extrait de code.
- **Groupe** &ndash; Les extraits de code sont regroupés dans le menu de contenu de l’extrait de code, à l’aide de cette valeur.
- **Description** &ndash; Explication de l’objectif de l’extrait de code.
- **Mime** &ndash; Contrôle dans quels types de fichiers l’extrait de code est disponible.
- **Est un modèle extensible** &ndash; Vérifiez que cette option est activée afin que l’extrait de code puisse être inséré au niveau du curseur en tapant le raccourci.
- **Est entouré du modèle** &ndash; Cochez cette option pour répertorier ce raccourci dans le menu de contenu **Entourer de...** dans l’éditeur.
- **Texte du modèle** &ndash; L’extrait de code réel qui sera inséré dans l’éditeur. Les espaces réservés de mots clés peuvent être définis en entourant un jeton de signes dollar, par exemple. `$type$`.
- **Panneau de propriété de mot clé** &ndash; Sur le côté droit de la fenêtre, utilisez la liste déroulante en haut pour choisir un mot clé (par exemple, `type`) et modifier des propriétés comme la valeur par défaut et l’info-bulle.

## <a name="using-keywords-in-the-editor"></a>Utilisation de mots clés dans l’éditeur

Pour utiliser un extrait de code avec des mots clés, comme celui défini ci-dessus, tapez le raccourci et appuyez sur **Tab** à deux reprises, et le contenu de l’extrait de code est inséré au niveau du curseur :

![Extrait de code inséré montrant les mots clés](media/source-editor-image12a.png)

Appuyez sur la touche **Tab** pour vous déplacer entre `object` et `MyProperty` afin de personnaliser l’extrait de code pour votre classe.

Un mot clé peut être répété dans un extrait de code, comme dans cet exemple `for`, où le mot clé `$i$` apparaît 3 fois :

![Modèle d’extrait de code avec des mots clés répétés](media/source-editor-image12b.png)

Dans l’éditeur, la touche **Tab** permet de basculer entre le premier `i` et `max`. En cas de refrappe de `i` avec un autre nom de variable, les trois instances sont mises à jour :

![Extrait de code inséré montrant des mots clés multiples](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Mots clés réservés

Il existe deux mots clés réservés que vous pouvez utiliser dans un extrait de code :

- `$selected$` &ndash; Si l’option **Est entouré du modèle** est activée dans l’extrait de code, ce mot clé sera remplacé par le texte qui a été mis en surbrillance dans l’éditeur lorsque l’extrait de code a été choisi.
- `$end$`&ndash; Lorsque l’utilisateur aura fini d’éditer les mots clés dans un extrait, `$end$` le curseur sera placé à l’emplacement du mot clé.

L’extrait de code `for` dans la section précédente est un exemple de ces deux mots clés réservés.

## <a name="see-also"></a>Voir aussi

- [Extraits de code (Visual Studio sur Windows)](/visualstudio/ide/code-snippets)
