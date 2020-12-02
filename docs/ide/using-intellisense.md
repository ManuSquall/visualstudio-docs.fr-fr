---
title: Informations sur les paramètres, liste des membres et informations express
description: 'Découvrez comment utiliser ces fonctionnalités IntelliSense : liste des membres, informations sur les paramètres, info Express et compléter le mot.'
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c60372d7268dd76bf9bbd967678490998ffa76c3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479015"
---
# <a name="intellisense-in-visual-studio"></a>IntelliSense dans Visual Studio

IntelliSense est une aide à la saisie semi-automatique de code qui comprend un certain nombre de fonctionnalités : Liste des membres, Informations sur les paramètres, Info Express et Compléter le mot. Ces fonctionnalités vous aident à en savoir plus sur le code que vous utilisez, à suivre les paramètres que vous entrez et à ajouter des appels aux propriétés et aux méthodes avec seulement quelques séquences de touches.

De nombreux aspects d'IntelliSense sont spécifiques au langage. Pour plus d'informations sur l’utilisation d’IntelliSense dans différents langages, consultez les rubriques répertoriées dans la section [Voir aussi](#see-also).

## <a name="list-members"></a>Liste des membres

Une liste de membres valides d'un type (ou d'un espace de noms) apparaît lorsque vous tapez un caractère déclencheur (par exemple, un point (`.`) en code managé ou `::` en C++). Si vous continuez à taper des caractères, la liste est filtrée pour inclure uniquement les membres qui commencent par ces caractères ou les membres dont le nom contient *un* mot qui commence par ces caractères. IntelliSense effectue également une mise en correspondance en « casse mixte ». Pour afficher les correspondances, vous pouvez donc simplement taper la première lettre de chaque mot en casse mixte composant le nom de membre.

Après avoir sélectionné un élément, vous pouvez l’insérer dans votre code en appuyant sur la touche **Tab** ou en tapant un espace. Si vous sélectionnez un élément et que vous tapez un point, l'élément apparaît suivi du point, ce qui provoque l'affichage d'une autre liste de membres. Lorsque vous sélectionnez un élément, mais avant de l'insérer, vous obtenez des informations express le concernant.

Dans la liste des membres, l'icône de gauche représente le type de membre, tel que l'espace de noms, la classe, la fonction ou la variable. Pour obtenir la liste des icônes, consultez [affichage de classes et icônes](../ide/class-view-and-object-browser-icons.md)de l’Explorateur d’objets. Si la liste est longue, appuyez sur **Pg. préc** et **Pg. suiv** pour vous déplacer vers le haut ou vers le bas dans la liste.

![Liste des membres Visual Studio](../ide/media/vs2015_intellisense.png)

Vous pouvez appeler la fonctionnalité **Liste des membres** manuellement en appuyant sur **Ctrl**+**J**, en choisissant **Edition** > **IntelliSense** > **Liste des membres** ou en choisissant le bouton **Liste des membres** dans la barre d’outils de l’éditeur. Lorsque la liste des membres est appelée sur une ligne vide ou en dehors d'une portée reconnue, elle affiche des symboles dans l'espace de noms global.

Pour désactiver par défaut la liste des membres (afin qu’elle n’apparaisse pas sauf si elle est appelée spécifiquement), accédez à **Outils**  >  **options**  >  **tous les langages** et désélectionnez **Répertorier automatiquement les membres**. Si vous souhaitez désactiver la liste des membres uniquement pour un langage spécifique, accédez à la page de paramètres **Général** pour ce langage.

Vous pouvez également passer en mode suggestion, où seul le texte que vous tapez est inséré dans le code. Par exemple, si vous entrez un identificateur qui ne figure pas dans la liste et que vous appuyez sur **Tab**, en mode de saisie semi-automatique, l’entrée remplace l’identificateur typé. Pour basculer entre le mode de saisie semi-automatique et le mode de suggestion, appuyez sur **CTRL** + **ALT** + **espace** ou choisissez **modifier** le mode de  >  **IntelliSense**  >  **saisie semi-automatique** IntelliSense.

## <a name="parameter-info"></a>Informations sur les paramètres

Informations sur les paramètres fournit des informations sur le nombre, les noms et les types des paramètres requis par une méthode, un paramètre de type générique d'attribut (en C#) ou un modèle (en C++).

Le paramètre suivant à taper pour la fonction vous est indiqué en gras. Pour les fonctions surchargées, vous pouvez utiliser les touches de direction **haut** et **bas** pour afficher d’autres informations sur les paramètres pour les surcharges de fonction.

![Informations sur les paramètres](../ide/media/vs2015_param_info.png)

Lorsque vous annotez des fonctions et des paramètres avec les commentaires de documentation XML, les commentaires apparaissent comme Informations sur les paramètres. Pour plus d’informations, consultez [Insérer des commentaires dans le code XML](reference/generate-xml-documentation-comments.md).

Vous pouvez appeler manuellement les informations sur les paramètres en choisissant **modifier**  >  **IntelliSense**  >  les informations sur les **paramètres** IntelliSense, en appuyant sur **CTRL** + **+** + **espace** ou en cliquant sur le bouton informations sur les **paramètres** dans la barre d’outils de l’éditeur.

## <a name="quick-info"></a>Infos express

Infos express affiche la déclaration complète de tout identificateur dans votre code.

![Info express Visual Studio](../ide/media/vs2015_quick_info.png)

Quand vous sélectionnez un membre dans la zone **Liste des membres**, l’info-bulle Info express s’affiche aussi.

![Informations sur les paramètres dans un fichier de code C&#35;](../ide/media/vs2015_paraminfo.png)

Vous pouvez appeler manuellement Info Express en choisissant **modifier**  >  **IntelliSense**  >  **Info Express** IntelliSense, en appuyant sur **CTRL** + **I** ou en cliquant sur le bouton **Info Express** dans la barre d’outils de l’éditeur.

Si une fonction est surchargée, il est possible que la fonctionnalité IntelliSense n'affiche pas les informations de toutes les formes de la surcharge.

Vous pouvez activer l’option infos rapides pour le code C++ en accédant à **Outils**  >  **options**  >  **éditeur de texte**  >  **C/C++**  >  **avancé** et en définissant **Info Express automatique** sur `false` .

## <a name="complete-word"></a>Compléter le mot

La fonctionnalité Compléter le mot entre automatiquement la fin du nom de variable, de commande ou de fonction dès que vous avez entré assez de caractères pour lever toute ambiguïté sur le nom. Vous pouvez appeler la fonctionnalité compléter le mot en choisissant **modifier**  >  **IntelliSense**  >  le **mot complet** IntelliSense, en appuyant sur **CTRL** + **espace** ou en choisissant le bouton **compléter le mot** dans la barre d’outils de l’éditeur.

## <a name="intellisense-options"></a>Options IntelliSense

Les options IntelliSense sont activées par défaut. Pour les désactiver, choisissez **Outils**  >  **options**  >  **éditeur de texte** et désélectionnez **informations sur les paramètres** ou **Répertorier automatiquement les membres** si vous ne souhaitez pas la fonctionnalité liste des membres.

## <a name="intellisense-icons"></a>Icônes IntelliSense
Les icônes dans IntelliSense peuvent indiquer une signification supplémentaire avec des modificateurs d’icône. Il s’agit d’étoiles, de cœurs et de verrous superposés à l’icône de l’objet, qui indiquent respectivement Protégé, Interne ou Privé.

|    Icône    |    Accessibilité    |    Description    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Modificateur d’icône « Public »](../ide/media/intellisensePublicNoModifier.png)       |    Classe publique    |    L’accès n’est pas limité.   |
| ![Modificateur d’icône « Protégé »](../ide/media/intellisenseProtectedModifier.png)       |    Classe protégée    |    L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.    |
| ![Modificateur d’icône « Interne protégé »](../ide/media/intellisenseProtectedInternalModifier.png)       |    Classe interne protégée    |    L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.    |
| ![Modificateur d’icône « Interne »](../ide/media/intellisenseInternalModifier.png)       |    Classe interne    |    L’accès est limité à l’assembly actuel.    |
|![Modificateur d’icône « Privé »](../ide/media/intellisensePrivateModifier.png)        |    Classe privée    |    L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur dans l’assembly actuel. (Disponible depuis C# 7.2.)    |

## <a name="troubleshoot-intellisense"></a>Résoudre les problèmes liés à IntelliSense

Dans certains cas, les options IntelliSense ne fonctionneront peut-être pas comme vous l'attendez.

**Le curseur se trouve en dessous d’une erreur de code.** Vous ne pourrez peut-être pas utiliser IntelliSense si une fonction incomplète ou une autre erreur existe dans le code situé au-dessus du curseur, car IntelliSense ne pourra peut-être pas analyser les éléments du code. Vous pouvez résoudre ce problème en commentant le code applicable.

**Le curseur se trouve dans un commentaire de code.** Vous ne pouvez pas utiliser IntelliSense si le curseur se trouve dans un commentaire de votre fichier source.

**Le curseur se trouve dans un littéral de chaîne.** Vous ne pouvez pas utiliser IntelliSense si le curseur se trouve entre les guillemets entourant un littéral de chaîne, comme dans l'exemple suivant :

```cpp
MessageBox( hWnd, "String literal|")
```

**Les options automatiques ne sont pas activées.** Par défaut, IntelliSense est automatiquement utilisé, mais vous pouvez le désactiver. Même lorsque la saisie semi-automatique des instructions est désactivée, vous pouvez appeler une fonctionnalité IntelliSense.

## <a name="see-also"></a>Voir aussi

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [IntelliSense de Python](../python/editing-python-code-in-visual-studio.md#intellisense)
- [IntelliSense JavaScript](../ide/javascript-intellisense.md)
- [Écrire et refactoriser du code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Insérer des commentaires dans le code XML](reference/generate-xml-documentation-comments.md)
