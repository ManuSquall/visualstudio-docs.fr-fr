---
title: "Substitution et extension des classes g&#233;n&#233;r&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, fournir des classes substituables"
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 15
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 15
---
# Substitution et extension des classes g&#233;n&#233;r&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Votre définition de langage DÉSOLÉ est une plateforme sur laquelle vous pouvez générer un puissant ensemble d'outils basés sur un langage spécifique au domaine.  De nombreuses extensions et les adaptations peuvent être accomplies en substituant et l'extension des classes générées de la définition de langage spécifique à un domaine.  Ces classes incluent pas simplement les classes de domaine que vous avez explicitement définies dans le schéma de définition DÉSOLÉ, mais également d'autres classes qui définissent la boîte à outils, l'explorateur, sérialisation, et ainsi de suite.  
  
## mécanismes d'extensibilité  
 Plusieurs mécanismes fournis pour vous permettre d'étendre le code généré.  
  
### méthodes de substitution dans une classe partielle  
 Les définitions de classe partielles permettent une classe à définir dans plusieurs emplacements.  Cela permet de séparer le code généré du code que vous écrivez vous\-même.  Dans votre code manuellement\-écrit, vous pouvez substituer des classes héritées par le code généré.  
  
 Par exemple, si dans la définition de votre DÉSOLÉ vous définissez une classe de domaine nommée `Book`, vous pouvez écrire du code personnalisé qui ajoute des méthodes override :  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Pour remplacer les méthodes dans une classe générée, écrivez toujours votre code dans un fichier séparé à partir de les fichiers générés.  En général, le fichier est contenu dans un dossier nommé CustomCode.  Si vous apportez des modifications au code généré, ils seront perdus lorsque vous régénérez le code de la définition de langage spécifique à un domaine.  
  
 Pour découvrir les méthodes vous pouvez substituer, la substitution de type dans la classe, suivi par un espace.  L'info\-bulle Intellisense indique quelles méthodes peuvent être substituées.  
  
### classes Double\-Dérivées  
 La plupart des méthodes dans les classes générées sont héritées d'un jeu fixe de classes dans les espaces de noms de modélisation.  Toutefois, certaines méthodes sont définies dans le code généré.  En général, cela signifie que vous ne pouvez pas les substituer ; vous ne pouvez pas remplacer dans une classe partielle les méthodes définies dans une autre définition partielle de la même classe.  
  
 Néanmoins, vous pouvez substituer ces méthodes en définissant l'indicateur de **génère double dérivé** pour la classe de domaine.  Cela provoque deux classes la génération, un correspondant à une classe de base abstraite de l'autre.  Toutes les définitions de méthode et de propriété sont dans la classe de base, et uniquement le constructeur est dans la classe dérivée.  
  
 Par exemple, dans l'exemple Library.dsl, la classe de domaine d' `CirculationBook` une valeur de propriété d' `Generates``Double Derived` à `true`.  Le code généré pour cette classe de domaine contient deux classes :  
  
-   `CirculationBookBase`, qui est un résumé et qui contient toutes les méthodes et propriétés.  
  
-   `CirculationBook`, qui est dérivé d' `CirculationBookBase`.  Elle est vide, à l'exception de ses constructeurs.  
  
 Pour substituer une méthode, vous créez une définition de la classe dérivée telle qu' `CirculationBook`.  vous pouvez substituer les méthodes générées et les méthodes héritées de l'infrastructure de modélisation.  
  
 Vous pouvez utiliser cette méthode avec tous les types d'éléments, notamment les éléments de modèle, des relations, des formes, des schémas, et les connecteurs.  Vous pouvez également substituer des méthodes d'autres classes générées.  certaines classes générées telles que le ToolboxHelper sont toujours double\-dérivées.  
  
### constructeurs personnalisés  
 vous ne pouvez pas substituer un constructeur.  Même dans les classes double\-dérivées, le constructeur doit se trouver dans la classe dérivée.  
  
 Si vous souhaitez fournir votre propre constructeur, il suffit de définir `Has Custom Constructor` pour la classe de domaine dans la définition de langage spécifique à un domaine.  Lorsque vous cliquez sur **Transformer tous les modèles**, le code généré n'inclura pas un constructeur pour cette classe.  Elle inclut un appel au constructeur manquant.  Ceci génère un rapport d'erreurs lorsque vous générez la solution.  Double\-cliquez sur le rapport d'erreurs pour afficher un commentaire dans du code généré qui explique ce que vous devez fournir.  
  
 Écrivez une définition de classe partielle dans un fichier distinct des fichiers générés, et fournissez le constructeur.  
  
### points marqués d'extension  
 Un point marqué d'extension est un emplacement dans la définition de langage spécifique à un domaine où vous pouvez définir une propriété ou une case à cocher pour indiquer que vous fournirez une méthode personnalisée.  les constructeurs personnalisés sont un exemple.  D'autres exemples incluent la définition `Kind` d'une propriété de domaine au stockage calculées ou personnalisé ou définir la balise d' **est personnalisé** dans un concepteur de connexion.  
  
 Dans chaque cas, lorsque vous définissez la balise et régénérez code, une erreur de build résulterez.  Double\-cliquez sur l'erreur pour afficher un commentaire qui explique ce que vous devez fournir.  
  
### Règles  
 Le gestionnaire de transactions permet de définir des règles qui s'exécutent avant une transaction pendant laquelle un événement indiqué s'est produit, tel qu'un changement d'une propriété.  Les règles sont généralement utilisées pour conserver le synchronisme entre les différents éléments dans le magasin.  Par exemple, les règles sont utilisées pour vous assurer que le diagramme affiche l'état actuel du modèle.  
  
 Les règles sont définies sur une base de par\-classe, vous n'avez pas avoir du code qui enregistre la règle pour chaque objet.  Pour plus d'informations, consultez [Règles de propagent les modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).  
  
### enregistrez les événements  
 Le magasin de modélisation fournit un mécanisme d'événement que vous pouvez utiliser pour écouter les types spécifiques de modification dans le magasin, y compris l'ajout et la suppression d'éléments, les modifications apportées aux valeurs de propriété, et ainsi de suite.  Les gestionnaires d'événements sont appelés après la fin de la transaction pendant laquelle les modifications ont été apportées.  En général, ces événements sont utilisés pour mettre à jour des ressources à l'extérieur de le magasin.  
  
### événements.NET  
 Vous pouvez vous abonner à des événements sur les formes.  Par exemple, vous pouvez écouter les clics de souris sur une forme.  Vous devez écrire le code qui s'abonne à l'événement pour chaque objet.  ce code peut être écrit dans une substitution d'InitializeInstanceResources\(\).  
  
 Certains événements sont générés sur ShapeFields, qui sont utilisés pour dessiner les éléments décoratifs sur une forme.  Pour obtenir un exemple, consultez [Comment : intercepter un événement Click sur une forme ou un décorateur](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md).  
  
 Ces événements généralement ne se produisent pas dans une transaction.  Vous devez créer une transaction si vous souhaitez effectuer des modifications dans le magasin.