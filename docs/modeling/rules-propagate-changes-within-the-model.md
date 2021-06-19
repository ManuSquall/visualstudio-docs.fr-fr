---
title: Propagation de modifications dans le modèle par des règles
description: Découvrez comment vous pouvez créer une règle de magasin pour propager une modification d’un élément à un autre dans le kit de développement logiciel (SDK) de visualisation et de modélisation (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bde67bd8375e3752370b3b815f8ed155d3123741
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387591"
---
# <a name="rules-propagate-changes-within-the-model"></a>Propagation de modifications dans le modèle par des règles
Vous pouvez créer une règle de magasin pour propager une modification d’un élément à un autre dans le kit de développement logiciel de visualisation et de modélisation (VMSDK). Lorsqu’une modification est apportée à un élément du magasin, des règles sont planifiées pour être exécutées, généralement lorsque la transaction la plus externe est validée. Il existe différents types de règles pour différents types d’événements, tels que l’ajout d’un élément ou sa suppression. Vous pouvez attacher des règles à des types spécifiques d’éléments, de formes ou de diagrammes. De nombreuses fonctionnalités intégrées sont définies par des règles : par exemple, les règles garantissent qu’un diagramme est mis à jour lorsque le modèle change. Vous pouvez personnaliser votre langage spécifique à un domaine en ajoutant vos propres règles.

 Les règles de stockage sont particulièrement utiles pour propager des modifications dans le magasin, c’est-à-dire des modifications apportées à des éléments de modèle, des relations, des formes ou des connecteurs, ainsi que leurs propriétés de domaine. Les règles ne s’exécutent pas lorsque l’utilisateur appelle les commandes d’annulation ou de rétablissement. Au lieu de cela, le gestionnaire de transactions vérifie que le contenu du magasin est restauré à l’état correct. Si vous souhaitez propager les modifications aux ressources en dehors du magasin, utilisez les événements du magasin. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Par exemple, supposons que vous souhaitiez spécifier que chaque fois que l’utilisateur (ou votre code) crée un nouvel élément de type ExampleDomainClass, un élément supplémentaire d’un autre type est créé dans une autre partie du modèle. Vous pouvez écrire un méthode AddRule et l’associer à ExampleDomainClass. Vous écrivez du code dans la règle pour créer l’élément supplémentaire.

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
> Le code d’une règle ne doit modifier que l’état des éléments contenus dans le magasin. autrement dit, la règle doit modifier uniquement les éléments de modèle, les relations, les formes, les connecteurs, les diagrammes ou leurs propriétés. Si vous souhaitez propager les modifications aux ressources en dehors du magasin, définissez des événements de magasin. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Pour définir une règle

1. Définissez la règle en tant que classe préfixé avec l' `RuleOn` attribut. L’attribut associe la règle à l’une de vos classes de domaine, relations ou éléments de diagramme. La règle est appliquée à chaque instance de cette classe, qui peut être abstraite.

2. Inscrivez la règle en l’ajoutant au jeu retourné par `GetCustomDomainModelTypes()` dans votre classe de modèle de domaine.

3. Dérivez la classe Rule de l’une des classes de règles abstraites et écrivez le code de la méthode d’exécution.

   Les sections suivantes décrivent ces étapes plus en détail.

### <a name="to-define-a-rule-on-a-domain-class"></a>Pour définir une règle sur une classe de domaine

- Dans un fichier de code personnalisé, définissez une classe et préfixez-la avec l' <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attribut :

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Le type d’objet dans le premier paramètre peut être une classe de domaine, une relation de domaine, une forme, un connecteur ou un diagramme. En règle générale, vous appliquez des règles aux classes de domaine et aux relations.

     `FireTime`Est généralement `TopLevelCommit` . Cela garantit que la règle est exécutée uniquement après que toutes les modifications principales de la transaction ont été effectuées. Les alternatives sont Inline, qui exécute la règle juste après la modification ; et LocalCommit, qui exécute la règle à la fin de la transaction actuelle (qui peut ne pas être la plus à l’extérieur). Vous pouvez également définir la priorité d’une règle pour qu’elle affecte son ordre dans la file d’attente, mais il s’agit d’une méthode non fiable pour obtenir le résultat dont vous avez besoin.

- Vous pouvez spécifier une classe abstraite comme type d’objet.

- La règle s’applique à toutes les instances de la classe subject.

- La valeur par défaut de `FireTime` est TimeToFire. TopLevelCommit. Cela provoque l’exécution de la règle lorsque la transaction la plus externe est validée. Une alternative est TimeToFire. Inline. Cela provoque l’exécution de la règle peu de temps après l’événement de déclenchement.

### <a name="to-register-the-rule"></a>Pour inscrire la règle

- Ajoutez votre classe Rule à la liste des types retournés par `GetCustomDomainModelTypes` dans votre modèle de domaine :

    ```csharp
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

- Si vous n’êtes pas sûr du nom de votre classe de modèle de domaine, examinez le fichier **Dsl\GeneratedCode\DomainModel.cs**

- Écrivez ce code dans un fichier de code personnalisé dans votre projet DSL.

### <a name="to-write-the-code-of-the-rule"></a>Pour écrire le code de la règle

- Dérivez la classe Rule de l’une des classes de base suivantes :

  | Classe de base | Déclencheur |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Un élément, un lien ou une forme est ajouté.<br /><br /> À utiliser pour détecter les nouvelles relations, en plus des nouveaux éléments. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Une valeur de propriété de domaine a été modifiée. L’argument de méthode fournit les valeurs anciennes et nouvelles.<br /><br /> Pour les formes, cette règle est déclenchée lorsque la propriété intégrée `AbsoluteBounds` change, si la forme est déplacée.<br /><br /> Dans de nombreux cas, il est plus pratique de remplacer `OnValueChanged` ou `OnValueChanging` dans le gestionnaire de propriétés. Ces méthodes sont appelées immédiatement avant et après la modification. En revanche, la règle s’exécute généralement à la fin de la transaction. Pour plus d’informations, consultez [gestionnaires de modification de valeur de propriété de domaine](../modeling/domain-property-value-change-handlers.md). **Remarque :**  Cette règle n’est pas déclenchée lors de la création ou de la suppression d’un lien. Au lieu de cela, écrivez un `AddRule` et un `DeleteRule` pour la relation de domaine. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Déclenché lorsqu’un élément ou un lien est sur le point d’être supprimé. La propriété ModelElement. IsDeleting a la valeur true jusqu’à la fin de la transaction. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Effectuée lorsqu’un élément ou un lien a été supprimé. La règle est exécutée une fois que toutes les autres règles ont été exécutées, y compris DeletingRules. ModelElement. IsDeleting a la valeur false, et ModelElement. IsDeleted a la valeur true. Pour permettre une annulation ultérieure, l’élément n’est pas réellement supprimé de la mémoire, mais il est supprimé de Store. ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Un élément est déplacé d’une partition de magasin à une autre.<br /><br /> (Notez que cela n’est pas lié à la position graphique d’une forme.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Cette règle s’applique uniquement aux relations de domaine. Elle est déclenchée si vous assignez explicitement un élément de modèle à l’une ou l’autre des extrémités d’un lien. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Déclenché lorsque l’ordre des liens vers ou à partir d’un élément est modifié à l’aide des méthodes MoveBefore ou MoveToIndex sur un lien. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Exécuté lorsqu’une transaction est créée. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Exécuté lorsque la transaction est sur le paragraphe d’être validée. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Exécuté lorsque la transaction va être restaurée. |

- Chaque classe a une méthode que vous substituez. Tapez `override` votre classe pour la découvrir. Le paramètre de cette méthode identifie l’élément en cours de modification.

  Notez les points suivants sur les règles :

1. L’ensemble des modifications apportées à une transaction peut déclencher de nombreuses règles. En règle générale, les règles sont exécutées lorsque la transaction la plus externe est validée. Ils sont exécutés dans un ordre non spécifié.

2. Une règle est toujours exécutée dans une transaction. Par conséquent, il n’est pas nécessaire de créer une nouvelle transaction pour apporter des modifications.

3. Les règles ne sont pas exécutées lorsqu’une transaction est restaurée, ou lorsque les opérations d’annulation ou de rétablissement sont effectuées. Ces opérations réinitialisent tout le contenu du magasin à son état précédent. Par conséquent, si votre règle modifie l’état de tout ce qui se trouve en dehors du magasin, il est possible qu’elle ne reste pas synchronisée avec le contenu du magasin. Pour mettre à jour l’État en dehors du magasin, il est préférable d’utiliser des événements. Pour plus d’informations, consultez les [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Certaines règles sont exécutées lorsqu’un modèle est chargé à partir d’un fichier. Pour déterminer si le chargement ou l’enregistrement est en cours, utilisez `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Si le code de votre règle crée davantage de déclencheurs de règles, ceux-ci sont ajoutés à la fin de la liste de déclenchement et sont exécutés avant la fin de la transaction. Les DeletedRules sont exécutés après toutes les autres règles. Une règle peut s’exécuter plusieurs fois dans une transaction, une fois pour chaque modification.

6. Pour passer des informations à des règles et à partir de celles-ci, vous pouvez stocker des informations dans le `TransactionContext` . Il s’agit simplement d’un dictionnaire qui est conservé pendant la transaction. Elle est supprimée à la fin de la transaction. Les arguments d’événement de chaque règle permettent d’y accéder. N’oubliez pas que les règles ne sont pas exécutées dans un ordre prévisible.

7. Utilisez les règles après avoir envisagé d’autres alternatives. Par exemple, si vous souhaitez mettre à jour une propriété en cas de modification d’une valeur, envisagez d’utiliser une propriété calculée. Si vous souhaitez limiter la taille ou l’emplacement d’une forme, utilisez un `BoundsRule` . Si vous souhaitez répondre à une modification d’une valeur de propriété, ajoutez un `OnValueChanged` Gestionnaire à la propriété. Pour plus d’informations, consultez [réponse aux modifications et propagation](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Exemple
 L’exemple suivant met à jour une propriété lorsqu’une relation de domaine est instanciée pour lier deux éléments. La règle est déclenchée non seulement lorsque l’utilisateur crée un lien sur un diagramme, mais également si le code de programme crée un lien.

 Pour tester cet exemple, créez un DSL à l’aide du modèle de solution de déroulement des tâches et insérez le code suivant dans un fichier dans le projet DSL. Générez et exécutez la solution, puis ouvrez l’exemple de fichier dans le projet de débogage. Dessinez un lien de commentaire entre une forme de commentaire et un élément de Flow. Le texte du commentaire change pour signaler l’élément le plus récent auquel vous vous êtes connecté.

 Dans la pratique, vous écrivez généralement un DeleteRule pour chaque méthode AddRule.

```csharp
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

- [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)