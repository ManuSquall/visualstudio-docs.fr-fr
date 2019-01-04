---
title: Interface utilisateur du débogueur (XSLT)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bd9ee5e1d86982b2e1b0a8495c9b43a14f43988
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875295"
---
# <a name="debugger-user-interface-xslt"></a>Interface utilisateur du débogueur (XSLT)

Cette rubrique décrit les fenêtres et boîtes de dialogue du débogueur. Elle ne présente que les parties de l'interface dont le comportement de débogage est spécifique à XSLT.

Pour plus d’informations, consultez le [référence de l’interface utilisateur de débogage](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Fenêtre Variables locales
 La fenêtre Variables locales affiche des informations sur les variables définies dans la feuille de style. Elle comporte trois colonnes d'informations :

 **Name**

 Cette colonne contient les noms de toutes les variables locales dans la portée actuelle. Les collections de nœuds ont un contrôle d’arborescence que vous pouvez explorer pour en voir les sous-dossiers.

 **Valeur**

 Cette colonne indique la valeur contenue dans chaque variable. Les nœuds d'attribut, d'instruction de traitement, de commentaire, de texte et CData affichent la valeur textuelle du nœud. Les nœuds d'espace de noms affichent l'URI de l'espace de noms.

 **Type**

 Cette colonne identifie le type de données de chaque variable répertoriée dans le **nom** colonne.

 La fenêtre Variables locales affiche également les variables de contexte prédéfinies qui servent au suivi du contexte de la transformation XSLT. Le tableau suivant décrit les variables de contexte prédéfinies utilisées par le débogueur XSLT.

|Nom|Description|
|-|-----------------|
|`last()`|Taille du contexte.|
|`position()`|Position (index) du nœud de contexte par rapport à la taille du contexte.|
|`self::node()`|Valeur du nœud de contexte.|

## <a name="output-window"></a>Fenêtre Sortie
 La fenêtre Sortie affiche les messages d'erreur éventuels ou les exceptions de sécurité qui se produisent pendant le débogage.

 Le débogueur XSLT utilise une fenêtre séparée pour afficher la sortie du débogueur. C’est la même fenêtre utilisée pour afficher la sortie à partir d’un **afficher la sortie XSLT** commande.

## <a name="task-list"></a>Liste des tâches
 Le **liste des tâches** répertorie toutes les erreurs de compilation dans la feuille de style. Si vous double-cliquez sur l'erreur, le curseur est déplacé jusqu'à la ligne contenant l'erreur.

 Le **liste des tâches** inclut toutes les erreurs qui se produisent dans les blocs de script dans le fichier XSLT.

> [!NOTE]
> Le débogueur XSLT n’a pas d’avertissements, afin qu’ils n’apparaissent jamais dans le **liste des tâches**.

## <a name="breakpoints-window"></a>Points d'arrêt (fenêtre)
 La fenêtre Points d'arrêt affiche tous les points d'arrêt définis dans le projet actuel. Si un point d'arrêt est ajouté pendant que la fenêtre est affichée, celle-ci est automatiquement mise à jour pour afficher le nouveau point.

 La fenêtre Points d'arrêt doit se comporter de la même façon que les autres débogueurs Visual Studio.

## <a name="command-windowimmediate-window"></a>Fenêtre de fenêtre/exécution de commande
 Pas implémentées dans cette mise en production du débogueur XSLT.

## <a name="watch-window"></a>Fenêtre Espion
 La fenêtre Espion permet d'évaluer les variables. Elle permet également de modifier la valeur des variables.

 Les variables affichées dans la fenêtre Espion sont celles du contexte actuel (l'élément de niveau supérieur de la pile d'appels). Si vous changez de contexte, cette fenêtre se met à jour et affiche les variables définies pour ce contexte.

## <a name="call-stack-window"></a>Fenêtre Pile des appels
 Le **pile des appels** fenêtre permet d’afficher les noms de fonctions sur la pile des appels, les types de paramètres et les valeurs de paramètre. Les informations de la pile d'appels ne sont affichées que lorsque le programme en cours de débogage est à l'arrêt.

 La pile d'appels représente les différents contextes par lesquels passe l'exécution du code XSLT. Par exemple, si un appel à partir du modèle est « a » au modèle « b », le modèle « a » et le modèle « b » s’affichent dans le **pile des appels** fenêtre avec le contexte actuel tout en haut de la liste. L'utilisateur peut ainsi voir la requête en cours d'exécution.

 Si les modèles n'ont pas de nom dans le fichier XSLT, les noms utilisés sont ceux générés par le processeur XSLT.

 Si vous cliquez sur un autre élément que celui situé en haut de la liste, les flèches vertes et le surlignage vert standard indiquent la création de branche de l’exécution XSLT.

## <a name="quickwatch-dialog-box"></a>Espion express (boîte de dialogue)
 Le **Espion express** boîte de dialogue est utilisée pour évaluer des expressions XPath 1.0. Le nœud de contexte (le nœud `self::node()` de la fenêtre Variables locales) est le contexte de l’exécution de l’expression XPath. Le résultat de l'exécution de l'expression XPath s'affiche dans la fenêtre Espion.

 La liste suivante décrit certaines limitations liées à l'évaluation des expressions XPath.

-   Seules les fonctions XPath intégrées sont autorisées.

-   Les fonctions XSLT intégrées, telles que `document()`, `key()`, etc., ne sont pas autorisées.

-   Les fonctions définies par l'utilisateur ne sont pas autorisées.

Pour plus d'informations, voir [Procédure : Évaluer une expression XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Code Machine (fenêtre)
 La fenêtre Code machine affiche le code machine généré par le compilateur XSLT. Elle peut s'utiliser de la même façon que toutes les autres fenêtres de code machine Visual Studio.

 Pour plus d’informations, [Comment : La fenêtre code machine](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Voir aussi

- [Débogage XSLT](../xml-tools/debugging-xslt.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)   
- [Inspecter des variables dans les fenêtres automatique et variables locales dans Visual Studio](../debugger/autos-and-locals-windows.md)