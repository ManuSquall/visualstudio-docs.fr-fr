---
title: "Interface utilisateur du d&#233;bogueur (XSLT) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Interface utilisateur du d&#233;bogueur (XSLT)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les fenêtres et boîtes de dialogue du débogueur.Elle ne présente que les parties de l'interface dont le comportement de débogage est spécifique à XSLT.  
  
 Pour plus d'informations, consultez [Référence du débogage de l'interface utilisateur](../debugger/debugging-user-interface-reference.md).  
  
## Fenêtre Variables locales  
 La fenêtre Variables locales affiche des informations sur les variables définies dans la feuille de style.Elle comporte trois colonnes d'informations :  
  
 **Nom**  
 Cette colonne contient les noms de toutes les variables locales dans la portée actuelle.Les collections de nœuds ont un contrôle d'arborescence que vous pouvez explorer pour en voir les sous\-dossiers.  
  
 **Valeur**  
 Cette colonne indique la valeur contenue dans chaque variable.Les nœuds d'attribut, d'instruction de traitement, de commentaire, de texte et CData affichent la valeur textuelle du nœud.Les nœuds d'espace de noms affichent l'URI de l'espace de noms.  
  
 **Type**  
 Cette colonne identifie le type de données de chaque variable répertoriée dans la colonne **Nom**.  
  
 La fenêtre Variables locales affiche également les variables de contexte prédéfinies qui servent au suivi du contexte de la transformation XSLT.Le tableau suivant décrit les variables de contexte prédéfinies utilisées par le débogueur XSLT.  
  
|Nom|Description|  
|---------|-----------------|  
|`last()`|Taille du contexte.|  
|`position()`|Position \(index\) du nœud de contexte par rapport à la taille du contexte.|  
|`self::node()`|Valeur du nœud de contexte.|  
  
 Pour plus d'informations, consultez [Comment : modifier le contexte du débogueur](../Topic/How%20to:%20Change%20the%20Debugger%20Context.md).  
  
## Fenêtre Sortie  
 La fenêtre Sortie affiche les messages d'erreur éventuels ou les exceptions de sécurité qui se produisent pendant le débogage.  
  
 Le débogueur XSLT utilise une fenêtre séparée pour afficher la sortie du débogueur.Il s'agit de la même fenêtre que celle utilisée pour afficher la sortie d'une commande **Afficher la sortie XSLT**.  
  
## Liste des tâches  
 La Liste des tâches répertorie toutes les erreurs de compilation rencontrées dans la feuille de style.Si vous double\-cliquez sur l'erreur, le curseur est déplacé jusqu'à la ligne contenant l'erreur.  
  
 La Liste des tâches inclut toutes les erreurs rencontrées dans les blocs de script du fichier XSLT.  
  
> [!NOTE]
>  Le débogueur XSLT ne produit pas d'avertissements. La Liste des tâches n'en comporte donc pas.  
  
## Fenêtre Points d'arrêt  
 La fenêtre Points d'arrêt affiche tous les points d'arrêt définis dans le projet actuel.Si un point d'arrêt est ajouté pendant que la fenêtre est affichée, celle\-ci est automatiquement mise à jour pour afficher le nouveau point.  
  
 La fenêtre Points d'arrêt doit se comporter de la même façon que les autres débogueurs Visual Studio.  
  
## Fenêtres Commande et Immédiat  
 Pas implémentées dans cette version du débogueur XSLT.  
  
## Fenêtre Espion  
 La fenêtre Espion permet d'évaluer les variables.Elle permet également de modifier la valeur des variables.  
  
 Les variables affichées dans la fenêtre Espion sont celles du contexte actuel \(l'élément de niveau supérieur de la pile d'appels\).Si vous changez de contexte, cette fenêtre se met à jour et affiche les variables définies pour ce contexte.  
  
## Fenêtre Pile des appels  
 La fenêtre Pile des appels permet d'afficher le nom des fonctions figurant dans la pile d'appels, les types de paramètres et les valeurs des paramètres.Les informations de la pile d'appels ne sont affichées que lorsque le programme en cours de débogage est à l'arrêt.  
  
 La pile d'appels représente les différents contextes par lesquels passe l'exécution du code XSLT.Par exemple, si le modèle « a » fait appel au modèle « b », tous deux s'affichent dans la fenêtre de la pile des appels, le contexte actuel apparaissant en tout début de liste.L'utilisateur peut ainsi voir la requête en cours d'exécution.  
  
 Si les modèles n'ont pas de nom dans le fichier XSLT, les noms utilisés sont ceux générés par le processeur XSLT.  
  
 Si vous cliquez sur un autre élément que celui situé en haut de la liste, les flèches vertes et le surlignage vert standard indiquent le branchement de l'exécution XSLT.  
  
## Boîte de dialogue Espion express  
 La boîte de dialogue **Espion express** permet d'évaluer des expressions XPath 1.0.Le nœud de contexte \(le nœud `self::node()` de la fenêtre Variables locales\) est le contexte de l'exécution de l'expression XPath.Le résultat de l'exécution de l'expression XPath s'affiche dans la fenêtre Espion.  
  
 La liste suivante décrit certaines limitations liées à l'évaluation des expressions XPath.  
  
-   Seules les fonctions XPath intégrées sont autorisées.  
  
-   Les fonctions XSLT intégrées, telles que `document()`, `key()`, etc., ne sont pas autorisées.  
  
-   Les fonctions définies par l'utilisateur ne sont pas autorisées.  
  
 Pour plus d'informations, consultez [Procédure : évaluer une expression XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## Fenêtre Code machine  
 La fenêtre Code machine affiche le code machine généré par le compilateur XSLT.Elle peut s'utiliser de la même façon que toutes les autres fenêtres de code machine Visual Studio.  
  
 Pour plus d'informations, consultez [Comment : utiliser la fenêtre Code Machine](../debugger/how-to-use-the-disassembly-window.md).  
  
## Voir aussi  
 [Débogage XSLT](../xml-tools/debugging-xslt.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Fenêtres de variables](../Topic/Variable%20Windows.md)