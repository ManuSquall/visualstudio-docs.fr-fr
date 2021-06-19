---
title: Validation dans un langage spécifique à un domaine
description: Découvrez comment vous pouvez définir des contraintes de validation pour vérifier que le modèle créé par l’utilisateur est explicite.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6de3a8940c845b29d2d0c7454b7c585f4676dba0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388332"
---
# <a name="validation-in-a-domain-specific-language"></a>Validation dans un langage spécifique à un domaine
En tant qu'auteur d'un langage spécifique à un domaine (DSL), vous pouvez définir des contraintes de validation afin de vérifier que le modèle créé par l'utilisateur a un sens. Par exemple, si votre DSL permet aux utilisateurs de tracer l'arbre généalogique d'une famille et de ses ancêtres, vous pouvez écrire une contrainte qui garantit que les enfants ont des dates de naissance postérieures à celles de leurs parents.

 Vous pouvez faire en sorte que les contraintes de validation s’exécutent lorsque le modèle est enregistré, lorsqu’il est ouvert, et lorsque l’utilisateur exécute explicitement la commande de menu **valider** . Vous pouvez aussi exécuter la validation sous le contrôle du programme. Par exemple, vous pouvez exécuter la validation en réponse à la modification d'une valeur de propriété ou d'une relation.

 La validation est particulièrement importante si vous écrivez des modèles de texte ou d’autres outils qui traitent les modèles de vos utilisateurs. La validation garantit que les modèles remplissent les conditions préalables assumées par ces outils.

> [!WARNING]
> Vous pouvez aussi autoriser que les contraintes de validation soient définies dans des extensions distinctes de votre DSL, en même temps que les gestionnaires de mouvements et les commandes de menu de l'extension. Les utilisateurs peuvent choisir d'installer ces extensions en plus de votre DSL. Pour plus d’informations, consultez [étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Exécution de la validation
 Quand un utilisateur modifie un modèle, à savoir, une instance de votre langage spécifique à un domaine, les actions suivantes peuvent exécuter la validation :

- Cliquez avec le bouton droit sur le diagramme et sélectionnez **valider tout**.

- Cliquez avec le bouton droit sur le nœud supérieur dans l’Explorateur de votre DSL et sélectionnez **valider tout** .

- Enregistrez le modèle.

- Ouvrez le modèle.

- En outre, vous pouvez écrire le code de programme qui exécute la validation comme partie d'une commande de menu ou en réponse à une modification, par exemple.

  Toutes les erreurs de validation s’affichent dans la fenêtre **liste d’erreurs** . L'utilisateur peut double-cliquer sur un message d'erreur pour sélectionner les éléments du modèle qui sont à l'origine de l'erreur.

## <a name="defining-validation-constraints"></a>Définition des contraintes de validation
 Vous définissez les contraintes de validation en ajoutant les méthodes de validation aux classes de domaine ou aux relations de votre DSL. Quand la validation est exécutée, que ce soit par l'utilisateur ou sous le contrôle du programme, tout ou partie des méthodes de validation est exécuté. Chaque méthode est appliquée à chaque instance de sa classe et il peut y avoir plusieurs méthodes de validation dans chaque classe.

 Chaque méthode de validation signale les erreurs éventuelles qu'elle détecte.

> [!NOTE]
> Les méthodes de validation signalent les erreurs, mais ne modifient pas le modèle. Si vous souhaitez ajuster ou empêcher certaines modifications, consultez [alternatives à la validation](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Pour définir une contrainte de validation

1. Activez la validation dans le nœud **Editor\Validation** :

   1. Ouvrez **Dsl\DslDefinition.DSL**.

   2. Dans l’Explorateur DSL, développez le nœud **éditeur** et sélectionnez **validation**.

   3. Dans la Fenêtre Propriétés, affectez à la propriété **utilise**  la valeur `true` . Il est plus pratique de définir toutes ces propriétés.

   4. Cliquez sur **transformer tous les modèles** dans la barre d’outils **Explorateur de solutions** .

2. Écrivez les définitions de classe partielle pour une ou plusieurs de vos classes de domaine ou relations de domaine. Écrivez ces définitions dans un nouveau fichier de code dans le projet **DSL** .

3. Préfixez chaque classe avec l'attribut suivant :

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Par défaut, cet attribut activera aussi la validation pour les classes dérivées. Si vous voulez désactiver la validation pour une classe dérivée spécifique, vous pouvez utiliser `ValidationState.Disabled`.

4. Ajoutez les méthodes de validation aux classes. Chaque méthode de validation peut avoir un nom quelconque, mais un seul paramètre de type <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.

    Elle doit être préfixée par un ou plusieurs attributs `ValidationMethod` :

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    L'attribut ValidationCategories spécifie à quel moment la méthode est exécutée.

   Exemple :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 Notez les points suivants relatifs au code :

- Vous pouvez ajouter des méthodes de validation aux classes de domaine ou relations de domaine. Le code de ces types se trouve dans **Dsl\Generated Code\Domain \* . cs**.

- Chaque méthode de validation s'applique à chaque instance de sa classe et de ses sous-classes. Dans le cas d'une relation de domaine, chaque instance est un lien entre deux éléments de modèle.

- Les méthodes de validation ne s'appliquent pas selon un ordre spécifié et chaque méthode ne s'applique pas aux instances de sa classe dans un ordre prévisible.

- Il n'est généralement pas recommandé qu'une méthode de validation mette à jour le contenu du magasin, car cela conduirait à des résultats incohérents. La méthode doit à la place signaler une erreur en appelant `context.LogError`, `LogWarning` ou `LogInfo`.

- Dans l'appel de LogError, vous pouvez fournir une liste d'éléments de modèle ou de liens de relation qui seront sélectionnés quand l'utilisateur double-clique sur le message d'erreur.

- Pour plus d’informations sur la façon de lire le modèle dans le code de programme, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

  L'exemple s'applique au modèle de domaine suivant. La relation ParentsHaveChildren possède des rôles nommés Child et Parent.

  ![Diagramme de définition DSL &#45; modèle d’arbre généalogique](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Catégories de validation
 Dans l'attribut <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>, vous spécifiez à quel moment la méthode de validation doit s'exécuter.

|Category|Exécution|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Lorsque l'utilisateur appelle la commande de menu Valider.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Lorsque le fichier de modèle est ouvert.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Lorsque le fichier est enregistré. S'il y a des erreurs de validation, l'utilisateur se voit offrir la possibilité d'annuler l'opération d'enregistrement.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Lorsque le fichier est enregistré. S'il y a des erreurs provenant des méthodes de la catégorie, l'utilisateur est prévenu qu'il peut ne pas être possible de rouvrir le fichier.<br /><br /> Utilisez cette catégorie pour les méthodes de validation qui testent la présence de noms ou ID dupliqués, ou autres conditions susceptibles de produire des erreurs de chargement.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Lorsque la méthode ValidateCustom est appelée. Les validations de cette catégorie ne peuvent être appelées qu'à partir du code de programme.<br /><br /> Pour plus d’informations, consultez [catégories de validation personnalisées](#custom).|

## <a name="where-to-place-validation-methods"></a>Où placer les méthodes de validation
 Vous pouvez souvent obtenir le même effet en plaçant une méthode de validation sur un type différent. Par exemple, vous pouvez ajouter une méthode à la classe Person au lieu de la relation ParentsHaveChildren et procéder à son itération à travers les liens :

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...
```

 **Regroupement des contraintes de validation.**  Pour appliquer la validation dans un ordre prévisible, définissez une méthode de validation unique sur une classe propriétaire, telle que l'élément racine de votre modèle. Cette technique permet aussi de regrouper plusieurs rapports d'erreur au sein d'un seul message.

 L'inconvénient est que la méthode combinée est moins facile à gérer et que les contraintes doivent toutes avoir les mêmes `ValidationCategories`. Il est donc recommandé que vous conserviez chaque contrainte dans une méthode distincte si possible.

 **Passage des valeurs dans le cache du contexte.**  Le paramètre de contexte dispose d'un dictionnaire dans lequel vous pouvez placer des valeurs arbitraires. Le dictionnaire demeure pendant la durée de l'exécution de la validation. Une méthode de validation particulière peut, par exemple, conserver le nombre d'erreurs dans le contexte et l'utiliser pour éviter que la fenêtre d'erreurs ne déborde sous les messages répétés. Exemple :

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Validation des multiplicités
 Les méthodes de validation pour vérifier la multiplicité minimale sont automatiquement générées pour votre DSL. Le code est écrit dans **Dsl\Generated Code\MultiplicityValidation.cs**. Ces méthodes prennent effet lorsque vous activez la validation dans le nœud **Editor\Validation** dans l’Explorateur DSL.

 Si vous définissez la multiplicité d'un rôle d'une relation de domaine sur 1..* ou 1..1, mais que l'utilisateur ne crée pas le lien de cette relation, un message d'erreur de validation s'affiche.

 Par exemple, si votre DSL a des classes Person et Town et une relation PersonLivesInTown avec une relation **1.. \\** * dans le rôle ville, un message d’erreur s’affiche pour chaque personne qui n’a pas de ville.

## <a name="running-validation-from-program-code"></a>Exécution de la validation à partir du code de programme
 Vous pouvez exécuter la validation en accédant à un ValidationController ou en en créant un. Si vous souhaitez que les erreurs soient affichées à l’utilisateur dans la fenêtre d’erreur, utilisez l’ValidationController joint au DocData de votre diagramme. Par exemple, si vous écrivez une commande de menu, `CurrentDocData.ValidationController` est disponible dans la classe de l'ensemble de commandes :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...
```

 Pour plus d’informations, consultez [Comment : ajouter une commande au menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Vous pouvez aussi créer un contrôleur de validation distinct et gérer les erreurs vous-même. Exemple :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}
```

## <a name="running-validation-when-a-change-occurs"></a>Exécution de la validation quand une modification intervient
 Si vous voulez vous assurer que l'utilisateur est immédiatement averti si le modèle devient non valide, vous pouvez définir un événement de magasin qui exécute la validation. Pour plus d’informations sur les événements de stockage, consultez [gestionnaires d’événements propager les modifications à l’extérieur du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 En plus du code de validation, ajoutez un fichier de code personnalisé à votre projet **DslPackage** , avec du contenu similaire à l’exemple suivant. Ce code utilise le `ValidationController` attaché au document. Ce contrôleur affiche les erreurs de validation dans la liste d’erreurs de Visual Studio.

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}
```

 Les gestionnaires sont aussi appelés après les opérations Annuler ou Rétablir qui affectent les liens ou les éléments.

## <a name="custom-validation-categories"></a><a name="custom"></a> Catégories de validation personnalisées
 En plus des catégories de validation standard, telles que Menu ou Ouvrir, vous pouvez définir vos propres catégories. Vous pouvez invoquer ces catégories à partir du code de programme. L'utilisateur ne peut pas les appeler directement.

 Une utilisation classique des catégories personnalisées consiste à définir une catégorie qui teste si le modèle satisfait aux conditions préalables d'un outil particulier.

 Pour ajouter une méthode de validation à une catégorie particulière, préfixez-la à l'aide d'un attribut comme suit :

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Vous pouvez préfixer une méthode avec autant d'attributs `[ValidationMethod()]` que vous le souhaitez. Vous pouvez ajouter une méthode aussi bien aux catégories personnalisées qu'aux catégories standard.

 Pour appeler une validation personnalisée :

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives-to-validation"></a><a name="alternatives"></a> Alternatives à la validation
 Les contraintes de validation signalent les erreurs, mais ne modifient pas le modèle. Si, à la place, vous voulez empêcher que le modèle ne devienne non valide, vous pouvez utiliser d'autres techniques.

 Cependant, ces techniques ne sont pas recommandées. Il est généralement préférable de laisser l'utilisateur décider de la façon dont un modèle non valide doit être corrigé.

 **Ajustez la modification pour rétablir la validité du modèle.**  Par exemple, si l'utilisateur définit une propriété au-dessus du maximum autorisé, vous pouvez réinitialiser la propriété à sa valeur maximale. Pour ce faire, définissez une règle. Pour plus d’informations, consultez [règles de propagation des modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).

 **Annulez la transaction en cas de modification non valide.** Vous pouvez également définir une règle à cet effet, mais dans certains cas, il est possible de substituer un gestionnaire de propriétés **OnValueChanging ()**, ou de substituer une méthode telle que `OnDeleted().` pour restaurer une transaction, utilisez `this.Store.TransactionManager.CurrentTransaction.Rollback().` pour plus d’informations, consultez [gestionnaires de modification de valeur de propriété de domaine](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Assurez-vous que l'utilisateur sache que la modification a été ajustée ou annulée. Par exemple, utilisez `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Propagation de modifications en dehors du modèle par des gestionnaires d'événements](../modeling/event-handlers-propagate-changes-outside-the-model.md)
