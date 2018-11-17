---
title: Modifier des diagrammes de séquence UML à l’aide de l’API UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f68cf87a7f45b906c6de43e0a837d49132b7a3e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725559"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Modifier des diagrammes de séquence à l'aide de l'API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une interaction est une séquence de messages entre un ensemble de lignes de vie. Une interaction est affichée sur un diagramme de séquence UML.  
  
 Pour obtenir des informations complètes sur l'API, consultez <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Pour obtenir une présentation plus générale à l’écriture de commandes et gestionnaires de mouvements pour les diagrammes UML, consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Code de base  
  
### <a name="namespace-imports"></a>Importations d'espaces de noms  
 Vous devez inclure les instructions `using` suivantes :  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Si vous créez des commandes de menu et des gestionnaires de mouvements, vous aurez aussi besoin du code suivant :  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Pour plus d’informations, consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Obtention du contexte  
 Si vous modifiez une interaction dans le cadre d'un gestionnaire de mouvements ou d'une commande dans un diagramme de séquence, vous pouvez obtenir une référence au contexte. Exemple :  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Diagrammes de séquence UML et diagrammes générés  
 Il existe deux types de diagrammes de séquence : ceux créés manuellement dans un projet de modélisation UML et ceux qui ont été générés à partir du code de programme. Utilisez la propriété `UmlMode` pour découvrir le diagramme de séquence que vous avez.  
  
> [!NOTE]
>  Cette propriété retourne la valeur false uniquement pour les diagrammes de séquence générés à partir du code à l'aide de Visual Studio 2013 et versions antérieures. Cela comprend les diagrammes de séquence générés par du code qui ont été migrés à partir de Visual Studio 2013 et versions antérieures. Cette version de Visual Studio ne prend pas en charge la génération de nouveaux diagrammes de séquence.  
  
 Par exemple, si vous souhaitez créer une commande de menu visible uniquement dans les diagrammes de séquence UML, la méthode `QueryStatus()` peut inclure l'instruction suivante :  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 Dans un diagramme de séquence généré, les lignes de vie, les messages et autres éléments sont essentiellement les mêmes que dans un diagramme de séquence UML. Dans un modèle UML, le magasin de modèles a une racine, qui est le modèle propriétaire de tous les autres éléments. Une interaction générée, quant à elle, existe dans son propre magasin de modèles, qui a une racine nulle :  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Pour créer et afficher une interaction  
 Créez l'interaction en tant qu'enfant d'un package ou d'un modèle.  
  
 Par exemple, si vous développez une commande qui peut être exécutée sur un diagramme de séquence vide, vous devez toujours commencer par vérifier si l'interaction existe.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Mise à jour d'une interaction et de sa disposition  
 Quand vous mettez à jour une interaction, terminez toujours l'opération en mettant à jour sa disposition à l'aide de l'une des méthodes suivantes :  
  
- `ISequenceDiagram.UpdateShapePositions()` ajuste les positions des formes qui ont été insérées ou déplacées récemment et leurs voisins.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` redessine le diagramme complet. Vous pouvez utiliser le paramètre pour spécifier le repositionnement des lignes de vie, des messages ou les deux.  
  
  Cela est particulièrement important quand vous insérez de nouveaux éléments ou déplacez des éléments existants. Ils ne seront pas dans les positions correctes dans le diagramme tant que vous n'aurez pas effectué l'une de ces opérations. Il vous suffit d'appeler l'une de ces opérations une seule fois à la fin d'une série de modifications.  
  
  Pour éviter de déconcerter l'utilisateur qui effectue une opération d'annulation après votre commande, utilisez un `ILinkedUndoTransaction` pour délimiter vos modifications et les opérations `Layout()` ou `UpdateShapePositions()` finales. Exemple :  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Pour utiliser un `ILinkedUndoTransaction`, vous devez effectuer la déclaration suivante dans votre classe :  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Pour plus d’informations, consultez [mises à jour du modèle UML de lien à l’aide de transactions](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Création d'une interaction  
  
### <a name="to-create-lifelines"></a>Pour créer des lignes de vie  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Une ligne de vie représente un élément connectable, autrement dit une instance d'un type. Par exemple, si l'interaction sert à montrer comment un composant délègue les messages entrants à ses parties internes, les lignes de vie peuvent représenter les ports et les parties du composant :  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Si l'interaction montre un ensemble arbitraire d'objets, vous pouvez également créer une propriété ou un autre `IConnectableElement` dans l'interaction elle-même :  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Comme alternative supplémentaire, vous pouvez définir le nom et le type d'une ligne de vie sans la lier à un élément connectable :  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>Pour créer des messages  
 Pour créer un message, vous devez identifier les points d'insertion sur les lignes de vie source et cible. Exemple :  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 Pour créer un message ayant une source ou une cible non définie  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Vous pouvez utiliser plusieurs messages pour identifier les points d'insertion à tous les points clés sur une ligne de vie :  
  
|Méthode sur ILifeline|À utiliser pour insérer à ce point|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|En haut de la ligne de vie.|  
|`FindInsertionPointAtBottom()`|En bas de la ligne de vie.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Un point situé immédiatement après le message spécifié.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Le point peut être sur la ligne de vie ou sur un bloc de spécification d'exécution parent.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Un point suivant une utilisation d'interaction.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Un point suivant un fragment combiné.|  
|`FindInsertionPoint(IExecutionSpecification block)`|En haut d'un bloc d'exécution.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|En haut d'un opérande d'un fragment combiné.|  
  
 Quand vous créez des messages, prenez soin d'éviter de définir un message qui traverserait un autre message.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Pour créer des fragments combinés et des utilisations d'interactions  
 Vous pouvez créer des fragments combinés et des utilisations d'interactions en spécifiant un point d'insertion sur chaque ligne de vie qui doit être couverte par l'élément. Prenez soin d'éviter de spécifier un ensemble de points qui traverserait un message ou un fragment existant.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 Vous pouvez aussi créer un fragment combiné qui couvre un ensemble de messages existant. Les messages doivent tous avoir comme source la même ligne de vie ou le même bloc d'exécution.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Un fragment combiné est toujours créé avec un seul opérande. Pour créer un opérande, vous devez spécifier l'opérande existant que vous souhaitez insérer avant ou après, et indiquer si vous souhaitez l'insérer avant ou après lui :  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Les formes apparaîtront dans des positions incorrectes si les modifications ne sont pas effectuées avec une opération `UpdateShapePositions()` ou `Layout()`.  
  
 La plupart des autres problèmes sont dus à des points d'insertion mal alignés, qui font que de nouveaux messages ou fragments devraient en traverser d'autres. Les symptômes peuvent être qu'aucune modification n'est effectuée ou qu'une exception est levée. L'exception peut n'être levée qu'au moment ou l'opération `UpdateShapePositions()` ou `Layout()` est effectuée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Définir un personnalisé élément de boîte à outils de modélisation](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)



