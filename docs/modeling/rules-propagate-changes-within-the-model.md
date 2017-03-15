---
title: "R&#232;gles de propagent les modifications dans le mod&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Langage spécifique à un domaine, de programmation des modèles de domaine"
  - "Langage spécifique à un domaine, les règles"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# R&#232;gles de propagent les modifications dans le mod&#232;le
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez créer une règle de magasin pour propager une modification d’un élément à un autre dans Visualization and Modeling SDK \(VMSDK\). En cas de modification à un élément dans le magasin, les règles sont planifiées pour être exécutée, le plus souvent lorsque la transaction la plus externe est validée. Il existe différents types de règles pour différents types d’événements, tels que l’ajout d’un élément, ou de le supprimer. Vous pouvez attacher des règles à des types spécifiques d’éléments, des formes ou des diagrammes. Nombreuses fonctions intégrées sont définies par des règles : par exemple, règles de vous assurer qu’un diagramme est mis à jour lorsque le modèle change. Vous pouvez personnaliser votre langage spécifique à un domaine en ajoutant vos propres règles.  
  
 Magasin de règles sont particulièrement utiles pour propager les modifications dans le magasin : autrement dit, des modifications aux éléments de modèle, relations, formes ou connecteurs et son domaine de propriétés. Les règles ne fonctionnent pas lorsque l’utilisateur appelle les commandes Annuler ou rétablir. Au lieu de cela, le Gestionnaire de transactions permet de s’assurer que le magasin de contenu est restauré à l’état correct. Si vous souhaitez propager les modifications aux ressources en dehors du magasin, utilisez stocker les événements. Pour plus d'informations, consultez [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Par exemple, supposons que vous souhaitez spécifier que chaque fois que l’utilisateur \(ou votre code\) crée un élément de type ExampleDomainClass, un élément supplémentaire d’un autre type est créé dans une autre partie du modèle. Vous pouvez écrire un AddRule et associez\-le à ExampleDomainClass. Vous pourriez écrire le code dans la règle pour créer l’élément supplémentaire.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  Le code d’une règle doit modifier l’état uniquement des éléments à l’intérieur de la banque ; Autrement dit, la règle doit modifier uniquement les éléments de modèle, les relations, formes, connecteurs, diagrammes ou leurs propriétés. Si vous souhaitez propager les modifications aux ressources en dehors du magasin, définissez stocker les événements. Pour plus d'informations, consultez [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### Pour définir une règle  
  
1.  Définissez la règle comme une classe préfixé avec la `RuleOn` attribut. L’attribut associe la règle à une de vos classes de domaine, les relations ou les éléments de diagramme. La règle sera appliquée à chaque instance de cette classe, qui peut être abstraite.  
  
2.  Enregistrer la règle en l’ajoutant à l’ensemble renvoyé par `GetCustomDomainModelTypes()` dans votre classe de modèle de domaine.  
  
3.  Une des classes abstraites règle dérivent de la classe de règle et écrivez le code de la méthode d’exécution.  
  
 Les sections suivantes décrivent ces étapes plus en détail.  
  
### Pour définir une règle sur une classe de domaine  
  
-   Dans un fichier de code personnalisé, définissez une classe et faites\-le précéder la <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attribut :  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Le type d’objet dans le premier paramètre peut être un classe de domaine, la relation de domaine, forme, connecteur ou un diagramme. En règle générale, appliquer des règles aux relations et aux classes de domaine.  
  
     Le `FireTime` est généralement `TopLevelCommit`. Cela garantit que la règle est exécutée uniquement une fois toutes les principales modifications de la transaction ont été apportées. Les alternatives sont en ligne, qui exécute la règle peu après la modification ; et LocalCommit, qui exécute la règle à la fin de la transaction actuelle \(qui ne peut pas être plus à l’extérieur\). Vous pouvez également définir la priorité d’une règle à affecter son classement dans la file d’attente, mais il s’agit d’une méthode non fiable d’atteindre le résultat souhaité.  
  
-   Vous pouvez spécifier une classe abstraite comme type d’objet.  
  
-   La règle s’applique à toutes les instances de la classe d’objet.  
  
-   La valeur par défaut `FireTime` est TimeToFire.TopLevelCommit. Cela provoque la règle à exécuter lors de la transaction la plus externe est validée. Une alternative consiste à TimeToFire.Inline. Cela provoque la règle doit être exécuté après l’événement de déclenchement.  
  
### Pour enregistrer la règle  
  
-   Ajoutez votre classe de règle à la liste des types retournée par `GetCustomDomainModelTypes` dans votre modèle de domaine :  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Si vous n’êtes pas sûr du nom de classe de modèle de domaine, recherchez dans le fichier **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   Écrire ce code dans un fichier de code personnalisé dans votre projet DSL.  
  
### Pour écrire le code de la règle  
  
-   Dérivez la classe de règle d’une des classes de base suivantes :  
  
    |Classe de base|Déclencheur|  
    |--------------------|-----------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Un élément, un lien ou une forme est ajoutée.<br /><br /> Cela permet de détecter de nouvelles relations, en plus des nouveaux éléments.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Modification d’une valeur de propriété de domaine. L’argument de méthode fournit les valeurs anciennes et nouvelles.<br /><br /> Pour les formes, cette règle est déclenchée lorsque intégré `AbsoluteBounds` modifications de propriété, si la forme est déplacée.<br /><br /> Dans de nombreux cas, il est plus pratique de remplacement `OnValueChanged` ou `OnValueChanging` dans le Gestionnaire de propriétés. Ces méthodes sont appelées immédiatement avant et après la modification. En revanche, la règle s’exécute généralement à la fin de la transaction. Pour plus d'informations, consultez [Gestionnaire de modification de la valeur de propriété du domaine](../modeling/domain-property-value-change-handlers.md). **Note:**  Cette règle n’est pas déclenchée lorsqu’un lien est créé ou supprimé. En revanche, écrire un `AddRule` et un `DeleteRule` pour la relation de domaine.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Déclenché lorsqu’un élément ou un lien est prêt à être supprimé. La propriété ModelElement.IsDeleting est true jusqu'à la fin de la transaction.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Effectuée lorsqu’un élément ou un lien a été supprimé. La règle est exécutée une fois toutes les autres règles ont été exécutées, y compris DeletingRules. ModelElement.IsDeleting a la valeur false et ModelElement.IsDeleted a la valeur true. Pour permettre une annulation ultérieure, l’élément n’est pas réellement supprimé de la mémoire, mais il est supprimé de Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Un élément est déplacé à partir de la partition d’un magasin à l’autre.<br /><br /> \(Notez que cela n’est pas liée à la position d’une forme graphique.\)|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Cette règle s’applique uniquement aux relations de domaine. Il est déclenché si vous affectez explicitement un élément de modèle à des extrémités d’un lien.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Déclenché lorsque l’ordre des liens vers ou à partir d’un élément est modifié à l’aide des méthodes MoveBefore ou MoveToIndex sur un lien.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Exécuté lorsqu’une transaction est créée.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Exécuté lorsque la transaction doit être validée.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Exécuté lorsque la transaction est sur le point d’être restaurée.|  
  
-   Chaque classe a une méthode que vous substituez. Type de `override` dans votre classe pour le détecter. Le paramètre de cette méthode identifie l’élément en cours de modification.  
  
 Notez les points suivants à propos des règles :  
  
1.  L’ensemble de modifications dans une transaction peut se déclencher de nombreuses règles. En règle générale, les règles sont exécutées lorsque la transaction la plus externe est validée. Ils sont exécutés dans un ordre non spécifié.  
  
2.  Une règle est toujours exécutée dans une transaction. Par conséquent, vous n’avez pas à créer une nouvelle transaction pour apporter des modifications.  
  
3.  Les règles ne sont pas exécutées lorsqu’une transaction est annulée, ou lors de l’annulation ou rétablissement des opérations. Ces opérations Réinitialiser tout le contenu de la banque à son état précédent. Par conséquent, si votre règle modifie l’état de quoi que ce soit en dehors du magasin, il ne peut pas conserver dans synchronism avec le magasin de contenu. Pour mettre à jour d’état en dehors du magasin, il est préférable d’utiliser des événements. Pour plus d'informations, consultez [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Certaines règles sont exécutées lorsqu’un modèle est chargé à partir du fichier. Pour déterminer si le chargement ou l’enregistrement est en cours, utilisez `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Si le code de votre règle crée plusieurs déclencheurs de règle, sera ajoutés à la fin de la liste de déclenchement, elles seront exécutées avant la fin de la transaction. DeletedRules sont exécutées après toutes les autres règles. Une règle peut exécuter plusieurs fois dans une transaction, une fois pour chaque modification.  
  
6.  Pour échanger des informations à partir de règles, vous pouvez stocker des informations dans le `TransactionContext`. Il s’agit simplement d’un dictionnaire qui est conservé pendant la transaction. Il est supprimé lorsque la transaction se termine. Les arguments d’événement de chaque règle fournissent un accès à celui\-ci. N’oubliez pas que les règles ne sont pas exécutées dans un ordre prévisible.  
  
7.  Utilisez les règles après avoir étudié les autres possibilités. Par exemple, si vous souhaitez mettre à jour une propriété lorsqu’une valeur change, envisagez d’utiliser une propriété calculée. Si vous souhaitez limiter la taille ou l’emplacement d’une forme, utilisez un `BoundsRule`. Si vous souhaitez répondre à une modification dans une valeur de propriété, ajoutez une `OnValueChanged` Gestionnaire à la propriété. Pour plus d'informations, consultez [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md).  
  
## Exemple  
 L’exemple suivant met à jour une propriété lorsqu’une relation de domaine est instanciée pour lier deux éléments. La règle sera déclenchée non seulement lorsque l’utilisateur crée un lien dans un diagramme, mais également si le code de programme crée un lien.  
  
 Pour tester cet exemple, créez un DSL à l’aide du modèle de solution de flux de tâches et insérez le code suivant dans un fichier dans le projet Dsl. Générer et exécuter la solution et ouvrez l’exemple de fichier dans le projet de débogage. Dessinez un lien de commentaire entre un commentaire et un élément de flux. Rapport sur l’élément plus récente que vous avez connectée à devient le texte du commentaire.  
  
 Dans la pratique, vous devez généralement écrire un DeleteRule pour chaque AddRule.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## Voir aussi  
 [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Définition de l'emplacement et de la taille de la forme par la classe BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)