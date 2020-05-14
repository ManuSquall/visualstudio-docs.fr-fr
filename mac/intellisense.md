---
title: IntelliSense
description: Informations sur l’utilisation d’IntelliSense dans Visual Studio pour Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405806"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense offre plusieurs fonctionnalités pour vous aider à améliorer l’expérience d’écriture et de modification du code. Par exemple, en plus de la complétion du code, le moteur IntelliSense fournit également des listes de membres, des informations sur les paramètres et des informations rapides.

Dans Visual Studio pour Mac, IntelliSense est fourni par le service principal de l’éditeur, et il est pris en charge dans de nombreux langages, comme C#, XAML, F#, JavaScript et d’autres. Visual Studio pour Mac offre aussi des fonctionnalités IntelliSense avancées, comme la possibilité de montrer des complétions provenant de bibliothèques qui ne sont pas encore importées dans le projet.

## <a name="code-completion"></a>Complétion du code

Quand vous tapez dans un fichier pris en charge, comme un fichier de code C#, les complétions pour la chaîne que vous tapez sont affichées dans une liste de complétions et sont mises à jour au fil de votre frappe. De plus, si vous supprimez du texte, la liste est remise à jour automatiquement pour inclure la plage la plus étendue de possibilités pour la complétion de la chaîne donnée. 

La fenêtre de complétion offre également la prise en charge du filtrage des complétions incluses par type. Par exemple, il est possible de limiter les membres de la liste de façon à représenter seulement des types comme les classes ou les délégués. Ce processus de filtrage peut être activé en cliquant sur une icône spécifique qui représente le type à filtrer ou via des raccourcis clavier correspondant à un type donné. Les icônes, situées dans le bas de la fenêtre de complétion, sont les suivantes :

| Icône                         | Nom          | Mot clé    | Touche d’accès rapide |
| -----------------------------|---------------| -----------|--------|
| ![Icône Classes](media/classes-icon.png)  | class         | `class`    |  ⌥C
| ![Icône de constante](media/constant-icon.png) | constant      | `const`    |  ⌥O
| ![Icône Délégué](media/delegate-icon.png) | délégué      | `delegate` |  ⌥D
| ![Icône Énumération](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Icône Événement](media/event-icon.png)    | événement         |            |  ⌥V
| ![Icône de champ](media/fields-icon.png)   | field         |            |  ⌥F
| ![Icône Interface](media/interface-icon.png)| interface     | `interface`|  ⌥I
| ![Icône Mot clé](media/keyword-icon.png)  | mot clé       |            |  ⌥K
| ![Icône Méthode](media/method-icon.png)   | method        |            |  ⌥M
| ![Icône Espace de noms](media/namespace-icon.png)| espace de noms     | `namespace`|  ⌥N
| ![Icône Propriétés](media/props-icon.png)    | propriété      |            |  ⌥P
| ![Icône Extrait de code](media/snippet-icon.png)  | extrait       | `class`    |  ⌥S
| ![Icône Structure](media/struct-icon.png)   | structure     | `struct`   |  ⌥S

En cliquant sur une des icônes ou en appuyant sur les touches de raccourci correspondantes, la liste de complétion se limite aux seuls types définis par l’ensemble de filtres.  

![Filtrage de type IntelliSense](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Fenêtre des paramètres

Une autre fonctionnalité d’IntelliSense est la possibilité de fournir une liste de paramètres là où c’est approprié. La liste de paramètres fournit des détails sur les signatures de méthode pour le code qui est appelé. En cliquant sur les flèches vers le haut et vers le bas dans la signature, vous pouvez parcourir chacune des signatures de paramètres disponibles pour déterminer le plus approprié pour vos besoins. En plus des détails des types de données autorisés, il peut également y avoir une description telle qu’elle est définie dans la méthode cible via des commentaires XML.

![Liste de paramètres](media/intellisense-parameter.png)

Quand vous renseignez les paramètres, le paramètre que vous éditez est en gras, tandis que les paramètres inactifs apparaissent dans leur police standard. 


## <a name="triggering-completion-window-and-parameter-window"></a>Déclenchement de la fenêtre de complétion et de la fenêtre des paramètres

La fenêtre de complétion est déclenchée automatiquement à mesure que vous tapez dans votre fichier source. Cependant, vous pouvez aussi déclencher la fenêtre de complétion en utilisant le raccourci `control-space`. Cette combinaison de touches fait que la liste de complétion apparaît à la position actuelle de votre point d’insertion. 

Vous pouvez également déclencher manuellement l’apparition de la fenêtre des paramètres en appuyant sur les touches `control-shift-space`. Quand votre point d’insertion se trouve à la position qui est valide pour une liste de paramètres, la liste des paramètres apparaît à côté de la position du point d’insertion.

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)
