---
title: 'Comment : accéder à et contraindre la sélection actuelle'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5d8fb0a2e5d218b76e972fc97a53afcd2f8ef3e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Comment : accéder à et contraindre la sélection actuelle

Lorsque vous écrivez un gestionnaire de mouvements ou de commandes pour votre langage spécifique à un domaine, vous pouvez déterminer quel élément cliqué par l’utilisateur. Vous pouvez également empêcher des formes ou des champs sélectionnés. Par exemple, vous pouvez organiser les que lorsque l’utilisateur clique sur un élément décoratif icône, la forme qui le contient est sélectionnée à la place. Contraindre la sélection de cette manière réduit le nombre de gestionnaires d’avoir à écrire. Elle facilite également pour l’utilisateur, ce qui vous pouvez cliquer sur n’importe où dans la forme sans avoir à éviter le decorator.

## <a name="access-the-current-selection-from-a-command-handler"></a>Accéder à la sélection actuelle à partir d’un gestionnaire de commandes

La commande set (classe) pour un langage spécifique à un domaine contient les gestionnaires de commandes pour des commandes personnalisées. Le <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> (classe), à partir de laquelle dérive la classe de jeu de commandes pour un langage spécifique à un domaine fournit quelques membres pour accéder à la sélection actuelle.

En fonction de la commande, le Gestionnaire de commandes peut-être la sélection dans le Générateur de modèles, l’Explorateur de modèle ou la fenêtre active.

### <a name="to-access-selection-information"></a>Pour accéder aux informations sur la sélection

1.  La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe définit les membres suivants qui peuvent être utilisés pour accéder à la sélection actuelle.

    |Membre|Description|
    |------------|-----------------|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Retourne `true` si un des éléments sélectionnés dans le Concepteur de modèle est une forme de compartiment ; sinon, `false`.|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Retourne `true` si le diagramme est sélectionné dans le Générateur de modèles ; sinon, `false`.|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Retourne `true` si un seul élément est sélectionné dans le Générateur de modèles ; sinon, `false`.|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Retourne `true` si un seul élément est sélectionné dans la fenêtre active ; sinon, `false`.|
    |Propriété <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtient une collection en lecture seule des éléments sélectionnés dans le Générateur de modèles.|
    |Propriété <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtient une collection en lecture seule des éléments sélectionnés dans la fenêtre active.|
    |Propriété <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtient l’élément principal de la sélection dans le Générateur de modèles.|
    |Propriété <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtient l’élément principal de la sélection dans la fenêtre active.|

2.  Le <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> propriété de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe fournit l’accès à la <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objet qui représente la fenêtre du Concepteur de modèles et fournit un accès supplémentaire les éléments sélectionnés dans le Générateur de modèles.

3.  En outre, le code généré définit une propriété de fenêtre outil Explorateur et une propriété de sélection de l’Explorateur dans la commande set, classe pour le langage spécifique à un domaine.

    -   La propriété de fenêtre outil Explorateur retourne une instance de la classe de fenêtre outil Explorateur pour le langage spécifique à un domaine. Dérive de la classe de fenêtre outil Explorateur la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> classe et représente l’Explorateur de modèles pour la langue spécifique à un domaine.

    -   Le `ExplorerSelection` propriété retourne l’élément sélectionné dans la fenêtre Explorateur de modèles pour la langue spécifique à un domaine.

## <a name="determine-which-window-is-active"></a>Déterminer quelle fenêtre est active

Le <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> contient de l’interface définit les membres qui fournissent l’accès à l’état actuel de la sélection dans l’interpréteur de commandes. Vous pouvez obtenir un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objet à partir de la classe de package ou de la commande set (classe) pour le langage spécifique à un domaine via le `MonitorSelection` propriété définie dans la classe de base de chaque. Dérive de la classe de package la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> classe et la classe de jeu de commande dérive la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Pour déterminer à partir d’un gestionnaire de commandes quel type de fenêtre est active

1.  Le <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> propriété de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe retourne une <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objet qui fournit l’accès à l’état actuel de la sélection dans l’interpréteur de commandes.

2.  Le <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> propriété de la <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interface Obtient le conteneur de sélection active, ce qui peut être différent de la fenêtre active.

3.  Ajoutez que les propriétés suivantes à la commande set, classe vous langage spécifique à un domaine pour déterminer quel type de fenêtre est active.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Contraindre la sélection

En ajoutant des règles de sélection, vous pouvez contrôler les éléments qui sont sélectionnées lorsque l’utilisateur sélectionne un élément dans le modèle. Par exemple, pour autoriser l’utilisateur à traiter un nombre d’éléments comme une unité unique, vous pouvez utiliser une règle de sélection.

### <a name="to-create-a-selection-rule"></a>Pour créer une règle de sélection

1.  Créez un fichier de code personnalisé dans le projet DSL

2.  Définissez une classe de règle de sélection qui est dérivée de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> classe.

3.  Remplacer la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> méthode de la classe de règle de sélection pour appliquer les critères de sélection.

4.  Ajouter une définition de classe partielle pour la classe ClassDiagram à votre fichier de code personnalisé.

     Le `ClassDiagram` classe dérive de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> classe et est défini dans le fichier de code généré, Diagram.cs, dans le projet DSL.

5.  Remplacer la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propriété de la `ClassDiagram` classe pour retourner la règle de sélection personnalisée.

     L’implémentation par défaut de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propriété obtient un objet de règle de sélection qui ne modifie pas la sélection.

### <a name="example"></a>Exemple

Le fichier de code suivant crée une règle de sélection qui étend la sélection pour inclure toutes les instances de chacune des formes de domaine qui a été initialement sélectionnée.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>