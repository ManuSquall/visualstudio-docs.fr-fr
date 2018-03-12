---
title: "Substitution et extension des Classes générées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f86600b6fd4bb272ece4454e9a94032ed05f3af1
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="overriding-and-extending-the-generated-classes"></a>Substitution et extension des classes générées
Définition de votre DSL est une plateforme sur laquelle vous pouvez créer un ensemble puissant d’outils qui sont basées sur un langage spécifique à un domaine. Plusieurs extensions et les adaptations est possible en substituant et en étendant les classes générées à partir de la définition DSL. Ces classes incluent non seulement les classes de domaine que vous avez définis explicitement dans le schéma de définition DSL, mais également d’autres classes qui définissent la boîte à outils, l’Explorateur, sérialisation et ainsi de suite.  
  
## <a name="extensibility-mechanisms"></a>Mécanismes d’extensibilité  
 Plusieurs mécanismes sont fournies pour vous permettre d’étendre le code généré.  
  
### <a name="overriding-methods-in-a-partial-class"></a>Méthodes de substitution dans une classe partielle  
 Définitions de classe partielles permettent à une classe d’être définie dans plusieurs emplacements. Cela vous permet de séparer le code généré à partir du code que vous écrivez vous-même. Dans votre code écrit manuellement, vous pouvez remplacer les classes héritées par le code généré.  
  
 Par exemple, si dans votre définition DSL, vous définissez une classe de domaine nommée `Book`, vous pouvez écrire du code personnalisé qui ajoute des méthodes override :  
  
 `public partial class Book`  
  
 `{`  
  
 `protected override void OnDeleting()`  
  
 `{`  
  
 `MessageBox.Show("Deleting book " + this.Title);`  
  
 `base.OnDeleting();`  
  
 `} }`  
  
> [!NOTE]
>  Pour substituer les méthodes dans une classe générée, vous devez toujours écrire votre code dans un fichier séparé à partir des fichiers générés. En règle générale, le fichier se trouve dans un dossier nommé CustomCode. Si vous apportez des modifications au code généré, elles seront perdues lorsque vous régénérez le code à partir de la définition DSL.  
  
 Pour découvrir les méthodes que vous pouvez substituer, tapez **remplacer** dans la classe, suivi d’un espace. L’info-bulle IntelliSense vous indique quelles méthodes peuvent être substituées.  
  
### <a name="double-derived-classes"></a>Classes dérivées en double  
 La plupart des méthodes dans les classes générées est héritée d’un ensemble fixe de classes dans les espaces de noms de modélisation. Toutefois, certaines méthodes sont définies dans le code généré. En règle générale, cela signifie que vous ne pouvez pas remplacer les ; dans une classe partielle, vous ne peut pas substituer les méthodes qui sont définies dans une autre définition partielle de la même classe.  
  
 Toutefois, vous pouvez substituer ces méthodes en définissant le **génère une Double dérivée** indicateur pour la classe de domaine. Cette causes deux classes à générer, celui qui est une classe de base abstraite de l’autre. Toutes les définitions de méthode et la propriété sont dans la classe de base, et seulement le constructeur est dans la classe dérivée.  
  
 Par exemple, dans l’exemple Library.dsl, le `CirculationBook` classe de domaine a la `Generates``Double Derived` propriété `true`. Le code généré pour cette classe de domaine contient deux classes :  
  
-   `CirculationBookBase`, qui est abstraite et qui contient toutes les méthodes et propriétés.  
  
-   `CirculationBook`, qui est dérivée de `CirculationBookBase`. Il est vide, à l’exception de ses constructeurs.  
  
 Pour remplacer n’importe quelle méthode, vous créez une définition partielle de la classe dérivée comme `CirculationBook`. Vous pouvez substituer les méthodes générées et les méthodes héritées de l’infrastructure de modélisation.  
  
 Vous pouvez utiliser cette méthode avec tous les types d’élément, y compris des connecteurs, des relations, des formes, des diagrammes et des éléments de modèle. Vous pouvez également substituer les méthodes d’autres classes générées. Certaines classes générées, telles que le ToolboxHelper sont toujours dérivées en double.  
  
### <a name="custom-constructors"></a>Constructeurs personnalisés  
 Vous ne pouvez pas remplacer un constructeur. Même dans les classes dérivées de double, le constructeur doit être dans la classe dérivée.  
  
 Si vous souhaitez fournir votre propre constructeur, cela en définissant `Has Custom Constructor` pour la classe de domaine dans la définition DSL. Lorsque vous cliquez sur **transformer tous les modèles**, le code généré n’inclut pas un constructeur de cette classe. Elle inclut un appel au constructeur manquant. Cela provoque un rapport d’erreurs lorsque vous générez la solution. Double-cliquez sur le rapport d’erreurs pour visualiser un commentaire dans le code généré qui explique ce que vous devez fournir.  
  
 Écriture d’une définition de classe partielle dans un fichier distinct à partir des fichiers générés et fournir le constructeur.  
  
### <a name="flagged-extension-points"></a>Points d’Extension avec indicateur  
 Un point d’extension avec indicateur est l’emplacement dans la définition DSL dans laquelle vous pouvez définir une propriété ou une case à cocher pour indiquer que vous fournissez une méthode personnalisée. Constructeurs personnalisés sont un exemple. Autres exemples de paramètre de la `Kind` d’une propriété de domaine à calculée ou stockage de personnalisée ou un paramètre le **personnalisé d’est** indicateur dans un générateur de connexion.  
  
 Dans chaque cas, lorsque vous définissez l’indicateur et régénérez le code, une erreur de build entraîne. Double-cliquez sur l’erreur pour afficher un commentaire qui explique ce que vous devez fournir.  
  
### <a name="rules"></a>Règles  
 Le Gestionnaire de transactions vous permet de définir les règles qui s’exécutent avant la fin d’une transaction dans laquelle un événement désigné s’est produite, tels qu’un changement dans une propriété. Règles sont généralement utilisées pour mettre à jour synchronism entre les différents éléments dans le magasin. Par exemple, les règles sont utilisées pour vous assurer que le diagramme affiche l’état actuel du modèle.  
  
 Les règles sont définies sur une base par classe, afin que vous n’avez pas pour que le code qui s’inscrit à la règle pour chaque objet. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).  
  
### <a name="store-events"></a>Stocker les événements  
 Le magasin de modélisation fournit un mécanisme d’événement que vous pouvez utiliser pour écouter les types spécifiques de modification dans le magasin, y compris l’ajout et la suppression d’éléments, les modifications apportées aux valeurs de propriété et ainsi de suite. Les gestionnaires d’événements sont appelées après la fermeture de la transaction dans laquelle les modifications ont été apportées. En règle générale, ces événements sont utilisés pour mettre à jour des ressources en dehors de la banque.  
  
### <a name="net-events"></a>Événements .NET  
 Vous pouvez vous abonner à certains événements sur les formes. Par exemple, vous pouvez écouter pour les clics de souris sur une forme. Vous devez écrire du code qui s’abonne à l’événement pour chaque objet. Ce code peut être écrit dans une substitution de InitializeInstanceResources().  
  
 Certains événements sont générés sur ShapeFields, qui sont utilisés pour dessiner les éléments décoratifs sur une forme. Pour obtenir un exemple, consultez [Comment : intercepter un clic sur une forme ou un élément décoratif](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Ces événements ne surviennent généralement pas à l’intérieur d’une transaction. Vous devez créer une transaction si vous souhaitez apporter des modifications dans le magasin.