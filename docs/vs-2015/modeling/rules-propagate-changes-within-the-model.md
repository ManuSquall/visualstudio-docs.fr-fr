---
title: Propagation de modifications dans le modèle de règles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 581d6d1f6e5923569f4d98705226d2336978bfc5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067558"
---
# <a name="rules-propagate-changes-within-the-model"></a>Propagation de modifications dans le modèle par des règles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer une règle de magasin pour propager une modification d’un élément à un autre dans la visualisation et modélisation de kit de développement logiciel (SDK) VISUALIZATION. En cas de modification à un élément dans le Store, les règles sont planifiées pour être exécutée, généralement lors de la transaction externe est validée. Il existe différents types de règles pour différents types d’événements, comme l’ajout d’un élément ou sa suppression. Vous pouvez attacher des règles à des types d’éléments, des formes ou des diagrammes. Nombreuses fonctionnalités intégrées sont définies par les règles : par exemple, règles garantissent qu’un diagramme est mis à jour quand le modèle change. Vous pouvez personnaliser votre langage spécifique à un domaine en ajoutant vos propres règles.  

 Règles de Store sont particulièrement utiles pour les modifications de propagation des modifications à l’intérieur de la banque : autrement dit, des propriétés pour les éléments de modèle, des relations, des formes ou des connecteurs et leur domaine. Les règles ne s’exécutent pas lorsque l’utilisateur appelle les commandes d’annulation ou de rétablissement. Au lieu de cela, le Gestionnaire de transactions permet de s’assurer que le magasin de contenu est restauré à l’état correct. Si vous souhaitez propager les modifications apportées aux ressources en dehors du magasin, utilisez les événements de Store. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors le modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  

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
>  Le code d’une règle doit modifier l’état uniquement des éléments à l’intérieur du Store ; Autrement dit, la règle doit modifier uniquement les éléments de modèle, les relations, formes, connecteurs, diagrammes ou leurs propriétés. Si vous souhaitez propager les modifications apportées aux ressources en dehors du magasin, définir des événements Store. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors le modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md)  

### <a name="to-define-a-rule"></a>Pour définir une règle  

1. Définir la règle comme une classe préfixé avec le `RuleOn` attribut. L’attribut associe la règle à une de vos classes de domaine, relations ou éléments de diagramme. La règle sera appliquée à chaque instance de cette classe, ce qui peut être abstraite.  

2. Enregistrer la règle en l’ajoutant à l’ensemble retourné par `GetCustomDomainModelTypes()` dans votre classe de modèle de domaine.  

3. Dérivez la classe de règle d’une des classes abstraites de règle et écrire le code de la méthode d’exécution.  

   Les sections suivantes décrivent ces étapes plus en détail.  

### <a name="to-define-a-rule-on-a-domain-class"></a>Pour définir une règle sur une classe de domaine  

- Dans un fichier de code personnalisé, définissez une classe et faites-la précéder le <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attribut :  

    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  

    ```  

- Le type d’objet dans le premier paramètre peut être une classe de domaine, la relation de domaine, la forme, la connecteur ou diagramme. En règle générale, vous appliquez des règles aux relations et classes de domaine.  

     Le `FireTime` est généralement `TopLevelCommit`. Cela garantit que la règle est exécutée uniquement une fois que les principales modifications de la transaction ont été apportées. Les alternatives sont Inline, qui exécute la règle peu après la modification ; et du LocalCommit, qui s’exécute à la règle à la fin de la transaction actuelle (qui ne peut pas être plus à l’extérieur). Vous pouvez également définir la priorité d’une règle à affecter son classement dans la file d’attente, mais il s’agit d’une méthode non fiable d’atteindre le résultat que vous avez besoin.  

- Vous pouvez spécifier une classe abstraite comme type d’objet.  

- La règle s’applique à toutes les instances de la classe d’objet.  

- La valeur par défaut `FireTime` est TimeToFire.TopLevelCommit. Cela provoque la règle à exécuter lorsque la transaction externe est validée. Une alternative consiste à TimeToFire.Inline. Cela provoque la règle doit être exécuté peu après l’événement de déclenchement.  

### <a name="to-register-the-rule"></a>Pour enregistrer la règle  

- Ajouter votre classe de règle à la liste des types retournés par `GetCustomDomainModelTypes` dans votre modèle de domaine :  

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

- Si vous n’êtes pas sûr du nom de votre classe de modèle de domaine, regardez dans le fichier **Dsl\GeneratedCode\DomainModel.cs**  

- Écrire ce code dans un fichier de code personnalisé dans votre projet DSL.  

### <a name="to-write-the-code-of-the-rule"></a>Pour écrire le code de la règle  

- Dérivez la classe de règle d’une des classes de base suivantes :  

  |                             Classe de base                              |                                                                                                                                                                                                                                                                                                                                                                              Déclencheur                                                                                                                                                                                                                                                                                                                                                                              |
  |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           <xref:Microsoft.VisualStudio.Modeling.AddRule>            |                                                                                                                                                                                                                                                                                                                        Un élément, un lien ou une forme est ajoutée.<br /><br /> Cela permet de détecter de nouvelles relations, en plus de nouveaux éléments.                                                                                                                                                                                                                                                                                                                        |
  |          <xref:Microsoft.VisualStudio.Modeling.ChangeRule>          | Une valeur de propriété de domaine est modifiée. L’argument de méthode fournit les valeurs anciennes et nouvelles.<br /><br /> Pour les formes, cette règle est déclenchée lorsque l’intégrée `AbsoluteBounds` des modifications de propriété, si la forme est déplacée.<br /><br /> Dans de nombreux cas, il est plus pratique substituer `OnValueChanged` ou `OnValueChanging` dans le Gestionnaire de propriétés. Ces méthodes sont appelées immédiatement avant et après la modification. En revanche, la règle s’exécute généralement à la fin de la transaction. Pour plus d’informations, consultez [gestionnaires de modification de valeur de propriété de domaine](../modeling/domain-property-value-change-handlers.md). **Remarque :**  Cette règle n’est pas déclenchée lorsqu’un lien est créé ou supprimé. En revanche, écrire un `AddRule` et un `DeleteRule` pour la relation de domaine. |
  |         <xref:Microsoft.VisualStudio.Modeling.DeletingRule>         |                                                                                                                                                                                                                                                                                                             Déclenché lorsqu’un élément ou un lien est sur le point d’être supprimé. La propriété ModelElement.IsDeleting vaut jusqu'à la fin de la transaction.                                                                                                                                                                                                                                                                                                              |
  |          <xref:Microsoft.VisualStudio.Modeling.DeleteRule>          |                                                                                                                                                                                                       Effectuée lorsqu’un élément ou un lien a été supprimé. La règle est exécutée une fois que toutes les autres règles ont été exécutées, y compris DeletingRules. ModelElement.IsDeleting a la valeur false et ModelElement.IsDeleted a la valeur true. Pour permettre une annulation ultérieure, l’élément n'est pas réellement supprimé de la mémoire, mais il est supprimé de Store.ElementDirectory.                                                                                                                                                                                                       |
  |           <xref:Microsoft.VisualStudio.Modeling.MoveRule>           |                                                                                                                                                                                                                                                                                                           Un élément est déplacé à partir de la partition d’un magasin vers un autre.<br /><br /> (Notez que cela n’est pas liée à la position d’une forme de graphique).                                                                                                                                                                                                                                                                                                            |
  |     <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>     |                                                                                                                                                                                                                                                                                                                 Cette règle s’applique uniquement aux relations de domaine. Elle est déclenchée si vous affectez explicitement un élément de modèle à chaque extrémité d’un lien.                                                                                                                                                                                                                                                                                                                 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> |                                                                                                                                                                                                                                                                                                                   Déclenché lorsque l’ordre des liens vers ou à partir d’un élément est modifié à l’aide des méthodes MoveBefore ou MoveToIndex sur un lien.                                                                                                                                                                                                                                                                                                                    |
  |   <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>   |                                                                                                                                                                                                                                                                                                                                                              Exécuté lorsqu’une transaction est créée.                                                                                                                                                                                                                                                                                                                                                              |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>   |                                                                                                                                                                                                                                                                                                                                                      Exécutée lorsque la transaction est sur le point d’être validée.                                                                                                                                                                                                                                                                                                                                                      |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>  |                                                                                                                                                                                                                                                                                                                                                     Exécutée lorsque la transaction est sur le point d’être restaurée.                                                                                                                                                                                                                                                                                                                                                     |

- Chaque classe a une méthode que vous substituez. Type `override` dans votre classe pour la détection. Le paramètre de cette méthode identifie l’élément qui est en cours de modification.  

  Notez les points suivants concernant les règles :  

1. L’ensemble de modifications dans une transaction peut déclencher plusieurs règles. En règle générale, les règles sont exécutées lorsque la transaction externe est validée. Ils sont exécutés dans un ordre non spécifié.  

2. Une règle est toujours exécutée dans une transaction. Par conséquent, vous n’êtes pas obligé de créer une nouvelle transaction pour apporter des modifications.  

3. Les règles ne sont pas exécutées lorsqu’une transaction est restaurée, ou lors de l’annulation ou rétablissement des opérations. Ces opérations Réinitialiser tout le contenu du Store à son état précédent. Par conséquent, si votre règle modifie l’état de quoi que ce soit à l’extérieur du Store, il ne peut pas conserver dans synchronism avec le Store contenu. Pour mettre à jour d’état à l’extérieur du Store, il est préférable d’utiliser des événements. Pour plus d’informations, consultez [gestionnaires propager les modifications en dehors le modèle d’événement](../modeling/event-handlers-propagate-changes-outside-the-model.md).  

4. Certaines règles sont exécutées lorsqu’un modèle est chargé à partir du fichier. Pour déterminer si le chargement ou l’enregistrement est en cours d’exécution, utilisez `store.TransactionManager.CurrentTransaction.IsSerializing`.  

5. Si le code de votre règle crée plusieurs déclencheurs de règle, ils seront ajoutés à la fin de la liste de déclenchement et seront exécutées avant la fin de la transaction. DeletedRules sont exécutés après toutes les autres règles. Une règle peut exécutées plusieurs fois dans une transaction, une fois pour chaque modification.  

6. Pour passer des informations à destination et à partir de règles, vous pouvez stocker les informations contenues dans le `TransactionContext`. Il s’agit simplement d’un dictionnaire qui est conservé pendant la transaction. Il est supprimé lorsque la transaction se termine. Les arguments d’événement dans chaque règle de fournissent un accès à celui-ci. N’oubliez pas que les règles ne sont pas exécutées dans un ordre prévisible.  

7. Utiliser les règles après avoir étudié les autres alternatives. Par exemple, si vous souhaitez mettre à jour une propriété lorsqu’une valeur change, envisagez d’utiliser une propriété calculée. Si vous souhaitez limiter la taille ou l’emplacement d’une forme, utilisez un `BoundsRule`. Si vous souhaitez répondre à une modification dans une valeur de propriété, ajoutez un `OnValueChanged` gestionnaire à la propriété. Pour plus d’informations, consultez [réponse en cours à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md).  

## <a name="example"></a>Exemple  
 L’exemple suivant met à jour une propriété lorsqu’une relation de domaine est instanciée pour lier deux éléments. La règle est déclenchée non seulement lorsque l’utilisateur crée un lien dans un diagramme, mais également si le code de programme crée un lien.  

 Pour tester cet exemple, créez un DSL à l’aide du modèle de solution flux de tâches et insérez le code suivant dans un fichier dans le projet Dsl. Générer et exécuter la solution et ouvrez l’exemple de fichier dans le projet de débogage. Dessinez un lien de commentaire entre une zone de commentaire et un élément de flux. Le texte dans les modifications de commentaire au rapport sur l’élément plus récente que vous avez connectée à.  

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
