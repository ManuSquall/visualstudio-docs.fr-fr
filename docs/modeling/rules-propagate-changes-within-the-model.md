---
title: "Règles de propagent les modifications dans le modèle | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: af086275f641e3237f8d22308c960ad30240b647
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>Propagation de modifications dans le modèle par des règles
Vous pouvez créer une règle de magasin pour propager une modification d’un élément à un autre dans Visualization and Modeling SDK (VMSDK). En cas de modification à un élément dans le magasin, les règles sont planifiées pour être exécutée, généralement lorsque la transaction externe est validée. Il existe différents types de règles pour différents types d’événements, tels que l’ajout d’un élément, ou de le supprimer. Vous pouvez attacher des règles à des types spécifiques d’éléments, des formes ou des diagrammes. De nombreuses fonctionnalités intégrées sont définies par des règles : par exemple, règles de vous assurer qu’un diagramme est mis à jour lorsque le modèle change. Vous pouvez personnaliser votre langage spécifique à un domaine en ajoutant vos propres règles.  
  
 Magasin de règles sont particulièrement utiles des modifications de propagation des modifications à l’intérieur de la banque - autrement dit, des propriétés pour les éléments de modèle, des relations, des formes ou des connecteurs et leur domaine. Les règles ne fonctionnent pas lorsque l’utilisateur appelle les commandes Annuler ou rétablir. Au lieu de cela, le Gestionnaire de transactions permet de s’assurer que le magasin de contenu est restauré dans l’état correct. Si vous souhaitez propager les modifications vers les ressources en dehors de la banque, utilisez stocker les événements. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors du modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Par exemple, supposons que vous souhaitez spécifier que chaque fois que l’utilisateur (ou votre code) crée un nouvel élément de type ExampleDomainClass, un élément supplémentaire d’un autre type est créé dans une autre partie du modèle. Vous pouvez écrire un AddRule et associez-le à ExampleDomainClass. Vous devez écrire le code dans la règle pour créer l’élément supplémentaire.  
  
```csharp  
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
  
    // Code here propagates change as required - for example:  
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
>  Le code d’une règle doit modifier l’état uniquement des éléments à l’intérieur du magasin ; Autrement dit, la règle doit modifier uniquement les éléments de modèle, des relations, formes, les connecteurs, diagrammes ou leurs propriétés. Si vous souhaitez propager les modifications vers les ressources en dehors de la banque, définissent des événements de magasin. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors du modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>Pour définir une règle  
  
1.  Définissez la règle comme une classe précédé la `RuleOn` attribut. L’attribut associe la règle avec l’un de vos classes de domaine, les relations ou des éléments de diagramme. La règle doit être appliquée à chaque instance de cette classe, ce qui peut être abstract.  
  
2.  Enregistrer la règle en l’ajoutant à l’ensemble retourné par `GetCustomDomainModelTypes()` dans votre classe de modèle de domaine.  
  
3.  Dérivez la classe de règle de l’une des classes abstraites de règle et écrire le code de la méthode d’exécution.  
  
 Les sections suivantes décrivent ces étapes plus en détail.  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>Pour définir une règle sur une classe de domaine  
  
-   Dans un fichier de code personnalisé, définissez une classe et faites-la précéder le <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attribut :  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value - but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Le type d’objet dans le premier paramètre peut être une classe de domaine, une relation de domaine, un forme, un connecteur ou un diagramme. En règle générale, vous appliquez des règles aux relations et aux classes de domaine.  
  
     Le `FireTime` est généralement `TopLevelCommit`. Cela garantit que la règle est exécutée uniquement après que toutes les modifications de la transaction principales ont été apportées. Les alternatives sont en ligne, qui exécute la règle peu après la modification ; et LocalCommit, qui exécute la règle à la fin de la transaction en cours (qui ne peut pas être plus à l’extérieur). Vous pouvez également définir la priorité d’une règle à affecter à son classement dans la file d’attente, mais il s’agit d’une méthode non fiable d’atteindre le résultat que vous avez besoin.  
  
-   Vous pouvez spécifier une classe abstraite comme type d’objet.  
  
-   La règle s’applique à toutes les instances de la classe d’objet.  
  
-   La valeur par défaut `FireTime` est TimeToFire.TopLevelCommit. Cela provoque la règle doit être exécutée lorsque la transaction externe est validée. Une autre solution consiste à TimeToFire.Inline. Cela provoque la règle doit être exécuté peu après l’événement de déclenchement.  
  
### <a name="to-register-the-rule"></a>Pour enregistrer la règle  
  
-   Ajoutez votre classe de règles à la liste des types retournés par `GetCustomDomainModelTypes` dans votre modèle de domaine :  
  
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
  
-   Si vous n’êtes pas sûr du nom de votre classe de modèle de domaine, recherchez dans le fichier **Dsl\GeneratedCode\DomainModel.cs**  
  
-   Écrire ce code dans un fichier de code personnalisé dans votre projet DSL.  
  
### <a name="to-write-the-code-of-the-rule"></a>Pour écrire le code de la règle  
  
-   Dérivez la classe de règle de l’une des classes de base suivantes :  
  
    |Classe de base|Déclencheur|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Un élément, un lien ou une forme est ajoutée.<br /><br /> Cela permet de détecter de nouvelles relations, en plus des nouveaux éléments.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Une valeur de propriété de domaine est modifiée. L’argument de méthode fournit les valeurs anciennes et nouvelles.<br /><br /> Pour les formes, cette règle est déclenchée lorsque la fonction intégrée `AbsoluteBounds` de propriété est modifiée, si la forme est déplacée.<br /><br /> Dans de nombreux cas, il est plus pratique remplacer `OnValueChanged` ou `OnValueChanging` dans le Gestionnaire de propriétés. Ces méthodes sont appelées immédiatement avant et après la modification. En revanche, la règle s’exécute généralement à la fin de la transaction. Pour plus d’informations, consultez [gestionnaires de modification de valeur de propriété domaine](../modeling/domain-property-value-change-handlers.md). **Remarque :** cette règle n’est pas déclenchée lorsqu’un lien est créé ou supprimé. À la place, écrire une `AddRule` et un `DeleteRule` pour la relation de domaine.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Déclenché lorsqu’un élément ou un lien est prêt à être supprimé. La propriété ModelElement.IsDeleting a la valeur true jusqu'à la fin de la transaction.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Effectuée lorsqu’un élément ou un lien a été supprimé. La règle est exécutée une fois toutes les autres règles ont été exécutées, y compris DeletingRules. ModelElement.IsDeleting a la valeur false et ModelElement.IsDeleted a la valeur true. Pour permettre une restauration ultérieure, l’élément n'est pas réellement supprimé de la mémoire, mais il est supprimé de Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Un élément est déplacé à partir de la partition d’un magasin vers un autre.<br /><br /> (Notez que cela n’est pas liée à la position de la forme de graphique).|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Cette règle s’applique uniquement aux relations de domaine. Elle est déclenchée si vous affectez explicitement un élément de modèle à des extrémités d’un lien.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Déclenché lorsque l’ordre des liens vers ou à partir d’un élément est modifié à l’aide des méthodes MoveBefore ou MoveToIndex sur un lien.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Exécuté lorsqu’une transaction est créée.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Exécuté lors de la transaction est sur le point d’être validée.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Exécuté lors de la transaction est sur le point d’être restaurée.|  
  
-   Chaque classe a une méthode que vous substituez. Type `override` dans votre classe pour la détection. Le paramètre de cette méthode identifie l’élément qui est en cours de modification.  
  
 Notez les points suivants à propos des règles :  
  
1.  L’ensemble de modifications dans une transaction peut se déclencher de nombreuses règles. En règle générale, les règles sont exécutées lorsque la transaction externe est validée. Elles sont exécutées dans un ordre non spécifié.  
  
2.  Une règle est toujours exécutée à l’intérieur d’une transaction. Par conséquent, vous n’avez pas à créer une nouvelle transaction pour apporter des modifications.  
  
3.  Les règles ne sont pas exécutées lorsqu’une transaction est annulée, ou lors de l’annulation ou rétablissement des opérations. Ces opérations Réinitialiser tout le contenu de la banque à son état précédent. Par conséquent, si votre règle modifie l’état de tout élément à l’extérieur de la banque, il ne peut pas conserver dans synchronism avec le magasin de contenu. Pour mettre à jour d’état en dehors de la banque, il est préférable d’utiliser des événements. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors du modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Certaines règles sont exécutées lorsqu’un modèle est chargé à partir du fichier. Pour déterminer si le chargement ou de l’enregistrement est en cours, utilisez `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Si le code de votre règle crée plusieurs déclencheurs de la règle, ils seront ajoutés à la fin de la liste de déclenchement et seront exécutées avant la fin de la transaction. DeletedRules sont exécutés après toutes les autres règles. Une règle peut exécuter plusieurs fois dans une transaction, une fois pour chaque modification.  
  
6.  Pour passer des informations à destination et à partir de règles, vous pouvez stocker des informations dans le `TransactionContext`. Il s’agit simplement d’un dictionnaire qui est conservé pendant la transaction. Il est supprimé lorsque la transaction se termine. Les arguments d’événement de chaque règle fournissent l’accès à celui-ci. N’oubliez pas que les règles ne sont pas exécutées dans un ordre prédéfini.  
  
7.  Utilisez les règles après prise en compte d’autres alternatives. Par exemple, si vous souhaitez mettre à jour d’une propriété lorsqu’une valeur est modifiée, envisagez d’utiliser une propriété calculée. Si vous souhaitez limiter la taille ou l’emplacement d’une forme, utilisez un `BoundsRule`. Si vous souhaitez répondre à une modification de la valeur d’une propriété, ajoutez une `OnValueChanged` gestionnaire à la propriété. Pour plus d’informations, consultez [réponse aux et propager les modifications](../modeling/responding-to-and-propagating-changes.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant met à jour une propriété lorsqu’une relation de domaine est instanciée pour lier deux éléments. La règle est déclenchée non seulement lorsque l’utilisateur crée un lien dans un diagramme, mais également si le code de programme crée un lien.  
  
 Pour tester cet exemple, créez DSL à l’aide du modèle de tâche de flux de solution et insérez le code suivant dans un fichier dans le projet Dsl. Générer et exécuter la solution et ouvrez l’exemple de fichier dans le projet de débogage. Dessinez un lien de commentaire entre une forme de commentaire et un élément de flux. Le texte du commentaire modifie un rapport sur l’élément plus récente que vous avez connectée à.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Emplacement et de la taille de la forme contrainte par BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)