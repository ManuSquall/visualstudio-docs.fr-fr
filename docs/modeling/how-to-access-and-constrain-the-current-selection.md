---
title: 'Comment : accéder à et contraindre la sélection actuelle'
description: Découvrez comment vous pouvez déterminer l’élément sur lequel l’utilisateur a cliqué avec le bouton droit lorsque vous écrivez un gestionnaire de commandes ou de mouvements pour votre langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28d0f99743535965b3cf203d461fac5d0193607c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386603"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Comment : accéder à et contraindre la sélection actuelle

Lorsque vous écrivez un gestionnaire de commandes ou de mouvements pour votre langage spécifique à un domaine, vous pouvez déterminer l’élément sur lequel l’utilisateur a cliqué avec le bouton droit. Vous pouvez également empêcher la sélection de certaines formes ou certains champs. Par exemple, vous pouvez faire en sorte que lorsque l’utilisateur clique sur l’élément décoratif d’une icône, la forme qui le contient est sélectionnée à la place. La restriction de la sélection de cette manière réduit le nombre de gestionnaires que vous devez écrire. Elle facilite également l’utilisateur, qui peut cliquer n’importe où dans la forme sans avoir à éviter l’élément décoratif.

## <a name="access-the-current-selection-from-a-command-handler"></a>Accéder à la sélection actuelle à partir d’un gestionnaire de commandes

La classe de jeu de commandes pour un langage spécifique à un domaine contient les gestionnaires de commandes de vos commandes personnalisées. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe, à partir de laquelle dérive la classe de jeu de commandes pour un langage spécifique à un domaine, fournit quelques membres pour accéder à la sélection actuelle.

Selon la commande, le gestionnaire de commandes peut avoir besoin de la sélection dans le générateur de modèles, l’Explorateur de modèles ou la fenêtre active.

### <a name="to-access-selection-information"></a>Pour accéder aux informations de sélection

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe définit les membres suivants qui peuvent être utilisés pour accéder à la sélection actuelle.

    |Membre|Description|
    |-|-|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Retourne `true` si l’un des éléments sélectionnés dans le générateur de modèles est une forme de compartiment ; sinon, `false` .|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Retourne `true` si le diagramme est sélectionné dans le concepteur de modèles ; sinon, `false` .|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Retourne `true` si un seul élément est sélectionné dans le concepteur de modèles ; sinon, `false` .|
    |Méthode <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Retourne `true` si un seul élément est sélectionné dans la fenêtre active ; sinon, `false` .|
    |Propriété<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Obtient une collection en lecture seule des éléments sélectionnés dans le générateur de modèles.|
    |Propriété<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Obtient une collection en lecture seule des éléments sélectionnés dans la fenêtre active.|
    |Propriété<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Obtient l’élément principal de la sélection dans le générateur de modèles.|
    |Propriété<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Obtient l’élément principal de la sélection dans la fenêtre active.|

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> propriété de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe fournit l’accès à l' <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> objet qui représente la fenêtre du concepteur de modèles et fournit un accès supplémentaire aux éléments sélectionnés dans le générateur de modèles.

3. En outre, le code généré définit une propriété de fenêtre outil Explorer et une propriété de sélection de l’Explorateur dans la classe de jeu de commandes pour le langage spécifique à un domaine.

    - La propriété de la fenêtre outil de l’Explorateur retourne une instance de la classe de fenêtre outil Explorer pour le langage spécifique à un domaine. La classe de fenêtre de l’outil Explorer dérive de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> classe et représente l’Explorateur de modèles pour le langage spécifique à un domaine.

    - La `ExplorerSelection` propriété retourne l’élément sélectionné dans la fenêtre Explorateur de modèles pour le langage spécifique à un domaine.

## <a name="determine-which-window-is-active"></a>Déterminer quelle fenêtre est active

L' <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interface contient définit des membres qui fournissent l’accès à l’état de sélection actuel dans le shell. Vous pouvez obtenir un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objet à partir de la classe de package ou de la classe de jeu de commandes pour le langage spécifique à un domaine via la `MonitorSelection` propriété définie dans la classe de base de chaque. La classe de package dérive de la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> classe, et la classe de jeu de commandes dérive de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Pour déterminer à partir d’un gestionnaire de commandes quel type de fenêtre est actif

1. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> propriété de la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe retourne un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> objet qui fournit l’accès à l’état de sélection actuel dans le shell.

2. La <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> propriété de l' <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interface obtient le conteneur de sélection actif, qui peut être différent de la fenêtre active.

3. Ajoutez les propriétés suivantes à la classe de jeu de commandes pour votre langage spécifique à un domaine afin de déterminer le type de fenêtre qui est actif.

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

En ajoutant des règles de sélection, vous pouvez contrôler les éléments qui sont sélectionnés lorsque l’utilisateur sélectionne un élément dans le modèle. Par exemple, pour permettre à l’utilisateur de traiter un certain nombre d’éléments comme une seule unité, vous pouvez utiliser une règle de sélection.

### <a name="to-create-a-selection-rule"></a>Pour créer une règle de sélection

1. Créer un fichier de code personnalisé dans le projet DSL

2. Définissez une classe de règle de sélection dérivée de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> classe.

3. Remplacez la <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> méthode de la classe de règle de sélection pour appliquer les critères de sélection.

4. Ajoutez une définition de classe partielle pour la classe ClassDiagram à votre fichier de code personnalisé.

     La `ClassDiagram` classe dérive de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> classe et est définie dans le fichier de code généré, Diagram. cs, dans le projet DSL.

5. Substituez la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propriété de la `ClassDiagram` classe pour retourner la règle de sélection personnalisée.

     L’implémentation par défaut de la <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> propriété obtient un objet de règle de sélection qui ne modifie pas la sélection.

### <a name="example"></a>Exemple

Le fichier de code suivant crée une règle de sélection qui étend la sélection de façon à inclure toutes les instances de chacune des formes de domaine initialement sélectionnées.

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