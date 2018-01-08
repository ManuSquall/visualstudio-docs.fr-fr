---
title: "Comment : modifier une commande de Menu Standard dans un langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: "10"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: f79852eae4b7dfae7345dbf6033a0e1cc0444250
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Comment : modifier une commande de menu standard dans un langage spécifique à un domaine
Vous pouvez modifier le comportement de certaines des commandes standard qui sont définies automatiquement dans votre DSL. Par exemple, vous pourriez modifier **couper** afin qu’il exclut les informations sensibles. Pour cela, vous devez substituer des méthodes dans une classe de jeu de commandes. Ces classes sont définies dans le fichier CommandSet.cs, dans le projet DslPackage, et son dérivées de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
 En résumé, pour modifier une commande :  
  
1.  [Découvrez ce que vous pouvez modifier des commandes](#what).  
  
2.  [Créer une déclaration partielle de la classe de jeu de commande appropriée](#extend).  
  
3.  [Substituer les méthodes ProcessOnStatus et ProcessOnMenu](#override) pour la commande.  
  
 Cette rubrique explique cette procédure.  
  
> [!NOTE]
>  Si vous souhaitez créer vos propres commandes de menu, consultez [Comment : ajouter une commande au Menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
##  <a name="what"></a>Les commandes peuvent modifier ?  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>Pour découvrir les commandes que vous pouvez modifier  
  
1.  Dans le `DslPackage` projet, ouvrez `GeneratedCode\CommandSet.cs`. Ce fichier c# se trouve dans l’Explorateur de solutions comme une filiale de `CommandSet.tt`.  
  
2.  Trouver les classes dans ce fichier se terminent par «`CommandSet`», par exemple `Language1CommandSet` et `Language1ClipboardCommandSet`.  
  
3.  Dans chaque classe de jeu de commandes, tapez « `override` » suivi d'un espace. IntelliSense affiche une liste des méthodes que vous pouvez substituer. Chaque commande à une paire de méthodes dont le nom commence par « `ProcessOnStatus` » et « `ProcessOnMenu` ».  
  
4.  Notez parmi les classes de jeu de commandes celle qui contient la commande à modifier.  
  
5.  Fermez le fichier sans enregistrer vos modifications.  
  
    > [!NOTE]
    >  En temps normal, vous ne devez pas modifier les fichiers qui ont été générés. Toute modification sera perdue lors de la prochaine génération des fichiers.  
  
##  <a name="extend"></a>Étendre la commande appropriée set (classe)  
 Créez un fichier qui contient une déclaration partielle de la classe de jeu de commandes.  
  
#### <a name="to-extend-the-command-set-class"></a>Pour développer la classe de jeu de commandes  
  
1.  Dans l'Explorateur de solutions, dans le projet DslPackage, ouvrez le dossier GeneratedCode, puis regardez sous CommandSet.tt et ouvrez son fichier généré CommandSet.cs. Notez l'espace de noms et le nom de la première classe qui y est définie. Par exemple, vous pouvez voir :  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  Dans **DslPackage**, créez un dossier nommé **Code personnalisé**. Dans ce dossier, créez un nouveau fichier de classe nommé `CommandSet.cs`.  
  
3.  Dans le nouveau fichier, écrivez une déclaration partielle dont l'espace de noms et le nom sont les mêmes que ceux de la classe partielle générée. Exemple :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **Remarque** si vous avez utilisé le modèle de fichier de classe pour créer le fichier, vous devez corriger l’espace de noms et le nom de classe.  
  
##  <a name="override"></a>Substituer les méthodes de commande  
 La plupart des commandes ont deux méthodes associées : la méthode avec un nom comme `ProcessOnStatus`... détermine si la commande doit être visible et activé. Elle est appelée chaque fois que l'utilisateur clique avec le bouton droit sur le diagramme et doit être exécutée rapidement et n'apporter aucune modification. `ProcessOnMenu`... est appelée lorsque l’utilisateur clique sur la commande et il doit exécuter la fonction de la commande. Vous souhaiterez peut-être substituer l'une ou l'autre de ces méthodes, ou les deux.  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>Pour modifier quand la commande apparaît dans un menu  
 Remplacer la ProcessOnStatus... (méthode). Cette méthode doit définir les propriétés Visible et Activé de son paramètre MenuCommand. En général, la commande examine this.CurrentSelection pour déterminer si elle s'applique aux éléments sélectionnés et peut également examiner leurs propriétés pour déterminer si elle peut être appliquée dans leur état actuel.  
  
 D'une manière générale, la propriété Visible doit être déterminée en fonction des éléments sélectionnés. La propriété Activé, qui détermine si la commande apparaît en noir ou en gris dans le menu, doit dépendre de l'état actuel de la sélection.  
  
 L'exemple suivant désactive l'élément de menu Delete quand l'utilisateur a sélectionné plusieurs formes.  
  
> [!NOTE]
>  Cette méthode n'a aucun impact sur la disponibilité de la commande par l'intermédiaire du clavier. Par exemple, la désactivation de l'élément de menu Delete n'empêche pas d'appeler la commande par l'intermédiaire de la touche Suppr.  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 Il est préférable d'appeler la méthode de base en premier, pour gérer tous les cas et les paramètres dont vous ne vous souciez pas.  
  
 La méthode ProcessOnStatus ne doit pas créer, supprimer ou mettre à jour des éléments dans le magasin.  
  
### <a name="to-change-the-behavior-of-the-command"></a>Pour modifier le comportement de la commande  
 Remplacer la ProcessOnMenu... (méthode). L'exemple suivant empêche l'utilisateur de supprimer plusieurs éléments à la fois, même à l'aide de la touche Suppr.  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 Si votre code modifie le magasin, par exemple s'il crée, supprime ou met à jour des éléments ou des liens, il doit le faire à l'intérieur d'une transaction. Pour plus d’informations, consultez [comment créer et mettre à jour des éléments de modèle](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Écriture du code des méthodes  
 Les fragments suivants sont souvent utiles dans ces méthodes :  
  
-   `this.CurrentSelection`. La forme sur laquelle l'utilisateur a cliqué avec le bouton droit est toujours incluse dans cette liste de formes et de connecteurs. Si l'utilisateur clique sur une partie vierge du diagramme, ce dernier est le seul membre de la liste.  
  
-   `this.IsDiagramSelected()` - `true`Si l’utilisateur a cliqué sur une partie vide du diagramme.  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()` - l'utilisateur n'a pas sélectionné plusieurs formes.  
  
-   `this.SingleSelection` - forme ou diagramme sur lequel l'utilisateur a cliqué avec le bouton droit.  
  
-   `shape.ModelElement as MyLanguageElement` - élément de modèle représenté par une forme.  
  
 Pour plus d’informations sur la façon de naviguer d’un élément à l’élément et sur la création des objets et des liens, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.Design.MenuCommand>   
 [Écriture de Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Comment : ajouter une commande au Menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tableau de commandes de Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence du schéma XML de VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [VMSDK - exemple de diagrammes du Circuit. Personnalisation de l’étendue de DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [Exemple de code : diagrammes de Circuit](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
