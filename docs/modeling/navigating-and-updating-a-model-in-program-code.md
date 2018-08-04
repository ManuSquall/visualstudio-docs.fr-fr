---
title: Navigation et mise à jour d'un modèle dans le code de programme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5bb0b27e57490f49dc677cffa553bc10201e5a47
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511338"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Accéder à un modèle et le mettre à jour dans le code du programme

Vous pouvez écrire du code pour créer et supprimer des éléments de modèle, définissez leurs propriétés et créer et supprimer des liens entre les éléments. Toutes les modifications doivent être effectuées dans une transaction. Si les éléments peuvent être affichés sur un diagramme, le diagramme sera « résolu « automatiquement à la fin de la transaction.

##  <a name="example"></a> Un exemple de définition DSL
 Il s’agit de la partie principale de DslDefinition.dsl pour les exemples de cette rubrique :

 ![Diagramme de définition DSL &#45; modèle d’arbre généalogique](../modeling/media/familyt_person.png)

 Ce modèle est une instance de cette solution DSL :

 ![Modèle d’arbre généalogique de la famille Tudor](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Espaces de noms et références
 Pour exécuter le code dans cette rubrique, vous devez référencer :

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Votre code utilisera cet espace de noms :

 `using Microsoft.VisualStudio.Modeling;`

 En outre, si vous écrivez le code dans un projet différent de celui dans lequel votre solution DSL est défini, vous devez importer l’assembly qui est généré par le projet Dsl.

##  <a name="navigation"></a> Navigation dans le modèle

### <a name="properties"></a>Properties
 Propriétés de domaine que vous définissez dans la définition DSL deviennent des propriétés auxquelles vous pouvez accéder dans le code de programme :

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Si vous souhaitez définir une propriété, vous devez le faire à l’intérieur d’un [transaction](#transaction):

 `henry.Name = "Henry VIII";`

 En cas de la définition DSL, une propriété **type** est **Calculated**, vous ne pouvez pas la définir. Pour plus d’informations, consultez [calculées et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relations
 Relations de domaine que vous définissez dans la définition DSL deviennent des paires de propriétés, l’autre sur la classe à chaque extrémité de la relation. Les noms des propriétés apparaissent dans le diagramme DslDefinition comme des étiquettes sur les rôles de chaque côté de la relation. En fonction de la multiplicité du rôle, le type de la propriété est la classe à l’autre extrémité de la relation, ou une collection de cette classe.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Les propriétés à deux extrémités d’une relation sont toujours réciproque. Lorsqu’un lien est créé ou supprimé, les propriétés du rôle sur les deux éléments sont mis à jour. L’expression suivante (qui utilise les extensions de `System.Linq`) est toujours vrai pour la relation ParentsHaveChildren dans l’exemple :

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Une relation est également représentée par un élément de modèle appelé un *lien*, qui est une instance du type de relation de domaine. Un lien a toujours l’élément d’une source et d’élément d’une cible. L’élément source et l’élément cible peuvent être le même.

 Vous pouvez accéder à un lien et ses propriétés :

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Par défaut, pas plus d’une instance d’une relation est autorisée à lier une paire d’éléments de modèle. Mais si, dans la définition DSL, le `Allow Duplicates` indicateur a la valeur true pour la relation, puis il peut y avoir plusieurs liens, et vous devez utiliser `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Il existe également d’autres méthodes pour accéder à des liens. Exemple :

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Rôles masqués.** En cas de la définition DSL, **est la propriété générée** est **false** pour un rôle particulier, puis aucune propriété n’est générée qui correspond à ce rôle. Toutefois, vous pouvez toujours accéder aux liens et parcourir les liens à l’aide des méthodes de la relation :

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 L’exemple plus fréquemment utilisée est la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relation qui lie un élément de modèle à la forme qui l’affiche sur un diagramme :

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Répertoire d’éléments
 Vous pouvez accéder à tous les éléments dans le magasin à l’aide de l’annuaire de l’élément :

 `store.ElementDirectory.AllElements`

 Il existe également des méthodes pour rechercher des éléments, tels que les éléments suivants :

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> L’accès aux informations de classe
 Vous pouvez obtenir des informations sur les classes, les relations et les autres aspects de la définition DSL. Exemple :

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Les classes de l’ancêtre d’éléments de modèle sont les suivantes :

-   ModelElement - tous les éléments et les relations sont ModelElements

-   ElementLink - toutes les relations sont ElementLinks

##  <a name="transaction"></a> Effectuer des modifications à l’intérieur d’une Transaction
 Chaque fois que votre code de programme change quelque chose dans le Store, elle doit le faire à l’intérieur d’une transaction. Cela s’applique à tous les éléments de modèle, relations, formes, diagrammes et leurs propriétés. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 La méthode la plus pratique de la gestion d’une transaction est avec un `using` instruction entre dans un `try...catch` instruction :

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Vous pouvez apporter autant de modifications à l’intérieur d’une seule transaction. Vous pouvez ouvrir les nouvelles transactions à l’intérieur d’une transaction active.

 Pour conserver vos modifications, vous devez `Commit` la transaction avant sa suppression. Si une exception se produit qui n’est pas interceptée dans la transaction, le Store réinitialisera à son état avant les modifications.

##  <a name="elements"></a> Création d’éléments de modèle
 Cet exemple ajoute un élément à un modèle existant :

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Cet exemple illustre ces points essentiels sur la création d’un élément :

-   Créer le nouvel élément dans une partition spécifique dans le Store. Pour les éléments de modèle et de relations, mais pas les formes, il s’agit généralement de la partition par défaut.

-   Rendre la cible d’une relation d’incorporation. Dans la DslDefinition de cet exemple, chaque personne doit être la cible de relation FamilyTreeHasPeople d’incorporation. Pour ce faire, nous pouvons définir la propriété de rôle FamilyTreeModel de l’objet personne ou ajouter la personne à la propriété de rôle de personnes de l’objet FamilyTreeModel.

-   Définir les propriétés d’un nouvel élément, en particulier la propriété pour laquelle `IsName` a la valeur true dans la DslDefinition. Cet indicateur marque la propriété qui sert à identifier l’élément de façon unique au sein de son propriétaire. Dans ce cas, la propriété Name a cet indicateur.

-   La définition DSL de cette solution DSL doit avoir été chargée dans le Store. Si vous écrivez une extension comme une commande de menu, ce sera généralement déjà true. Dans d’autres cas, vous pouvez explicitement charger le modèle dans le Store, ou utiliser <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> pour le charger. Pour plus d’informations, consultez [Comment : ouvrir un modèle depuis un fichier de Code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).

 Lorsque vous créez un élément de cette façon, une forme est automatiquement créée (si la solution DSL possède un diagramme). Il apparaît dans un emplacement automatiquement affecté, avec d’autres fonctionnalités, la couleur et la forme par défaut. Si vous souhaitez contrôler où et comment la forme associée s’affiche, consultez [création d’un élément et sa forme](#merge).

##  <a name="links"></a> Création de liens de relation
 Il existe deux relations définies dans l’exemple de définition DSL. Chaque relation définit un *propriété de rôle* sur la classe à chaque extrémité de la relation.

 Il existe trois façons dans lequel vous pouvez créer une instance d’une relation. Chacune de ces trois méthodes a le même effet :

-   Définissez la propriété de l’acteur de rôle source. Exemple :

    -   `familyTree.People.Add(edward);`

    -   `edward.Parents.Add(henry);`

-   Définissez la propriété de l’acteur de rôle cible. Exemple :

    -   `edward.familyTreeModel = familyTree;`

         La multiplicité de ce rôle est `1..1`, donc nous attribuons la valeur.

    -   `henry.Children.Add(edward);`

         La multiplicité de ce rôle est `0..*`, de sorte que nous ajoutons à la collection.

-   Construire explicitement une instance de la relation. Exemple :

    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

 La dernière méthode est utile si vous souhaitez définir des propriétés sur la relation proprement dite.

 Lorsque vous créez un élément de cette façon, un connecteur sur le diagramme est automatiquement créé, mais il a une forme par défaut, la couleur et autres fonctionnalités. Pour contrôler la façon dont le connecteur associé est créé, consultez [création d’un élément et sa forme](#merge).

##  <a name="deleteelements"></a> La suppression d’éléments
 Supprimer un élément en appelant `Delete()`:

 `henry.Delete();`

 Cette opération supprimera également :

-   Liens de relation vers et à partir de l’élément. Par exemple, `edward.Parents` ne contient plus de `henry`.

-   Éléments à des rôles pour lesquels le `PropagatesDelete` indicateur a la valeur true. Par exemple, la forme qui affiche l’élément sera supprimée.

 Par défaut, chaque relation d’incorporation a `PropagatesDelete` true au niveau du rôle cible. Suppression `henry` ne supprime pas le `familyTree`, mais `familyTree.Delete()` supprime tous les `Persons`. Pour plus d’informations, consultez [personnalisation du comportement de suppression](../modeling/customizing-deletion-behavior.md).

 Par défaut, `PropagatesDelete` n’est pas vrai pour les rôles de relations de référence.

 Vous pouvez provoquer les règles de suppression omettre les propagations spécifiques lorsque vous supprimez un objet. Cela est utile si vous remplacez un seul élément d’une autre. Vous fournissez le GUID d’un ou plusieurs rôles pour lesquels la suppression ne doit pas être propagée. Le GUID peut être obtenu à partir de la classe de relation :

 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

 (Cet exemple particulier n’a aucun effet, étant donné que `PropagatesDelete` est `false` pour les rôles de la `ParentsHaveChildren` relation.)

 Dans certains cas, la suppression est interdite par l’existence d’un verrou, sur l’élément ou sur un élément qui serait supprimé par propagation. Vous pouvez utiliser `element.CanDelete()` pour vérifier si l’élément peut être supprimé.

##  <a name="deletelinks"></a> Suppression des liens de relation
 Vous pouvez supprimer un lien de relation en supprimant un élément à partir d’une propriété de rôle :

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Vous pouvez également supprimer le lien explicitement :

 `edwardHenryLink.Delete();`

 Ces trois méthodes ont toutes le même effet. Vous devez uniquement utiliser un d’eux.

 Si le rôle a une multiplicité de valeur 0.. 1 ou 1.. 1, vous pouvez la définir sur `null`, ou à une autre valeur :

 `edward.FamilyTreeModel = null;` ou :

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Réorganisation les liens d’une relation
 Les liens d’une relation particulière qui sont source ou ciblé sur un élément de modèle particulier ont un ordre spécifique. Ils apparaissent dans l’ordre dans lequel ils ont été ajoutés. Par exemple, cette instruction donne toujours les enfants dans le même ordre :

 `foreach (Person child in henry.Children) ...`

 Vous pouvez modifier l’ordre des liens :

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Verrous
 Vos modifications peuvent être évitées en un verrou. Verrous peuvent être définies sur des éléments individuels sur les partitions et sur le magasin. Si un de ces niveaux possède un verrou qui empêche le type de modification que vous souhaitez apporter, une exception peut levée lorsque vous essayez d’elle. Vous pouvez découvrir si les verrous sont définis à l’aide d’élément. GetLocks(), qui est une méthode d’extension qui est définie dans l’espace de noms <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Pour plus d’informations, consultez [définition d’une stratégie de verrouillage pour créer des Segments en lecture seule](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Copier et coller
 Vous pouvez copier des éléments ou des groupes d’éléments à un <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Les éléments sont stockés en tant qu’un groupe d’élément sérialisé.

 Vous pouvez fusionner des éléments à partir d’un IDataObject dans un modèle :

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` peut accepter soit un `PresentationElement` ou un `ModelElement`. Si vous lui donnez un `PresentationElement`, vous pouvez également spécifier une position sur le diagramme cible en tant que troisième paramètre.

##  <a name="diagrams"></a> Navigation et mise à jour des diagrammes
 Dans une solution DSL, l’élément de modèle de domaine, qui représente un concept telles que la personne ou à une chanson, est distincte de l’élément de forme, qui représente ce que vous voyez sur le diagramme. L’élément de modèle de domaine stocke les propriétés importantes et les relations des concepts. L’élément de forme stocke la taille, la position et la couleur de la vue de l’objet sur le diagramme et la disposition de ses composants.

### <a name="presentation-elements"></a>Éléments de présentation
 ![Diagramme de classes de la forme de base et des types d'éléments](../modeling/media/dslshapesandelements.png)

 Dans votre définition DSL, chaque élément que vous spécifiez crée une classe qui est dérivée d’une des classes standards suivantes.

|Type d’élément|Classe de base|
|---------------------|----------------|
|Classe de domaine|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relation de domaine|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Forme|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Connecteur|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagramme|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Un élément dans un diagramme représente généralement un élément de modèle. Généralement (mais pas toujours), un <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> représente une instance de classe de domaine et un <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> représente une instance de relation de domaine. Le <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relation lie une forme de nœud ou un lien à l’élément de modèle qu’il représente.

 Chaque forme de nœud ou lien appartient à un diagramme. Une forme de lien binaire connecte deux formes de nœud.

 Formes peuvent avoir des formes enfants dans deux jeux. Une forme dans le `NestedChildShapes` ensemble ne se limite à la zone englobante de son parent. Une forme dans le `RelativeChildShapes` liste peut apparaître en dehors ou en partie en dehors des limites du parent - par exemple une étiquette ou un port. Un diagramme n’a aucun `RelativeChildShapes` et aucun `Parent`.

###  <a name="views"></a> Navigation entre les formes et les éléments
 Les éléments de modèle de domaine et des éléments de forme sont liés par le <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relation.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 La même relation lie des relations aux connecteurs sur le diagramme :

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Cette relation lie également la racine du modèle vers le diagramme :

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Pour obtenir l’élément de modèle représenté par une forme, utilisez :

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navigation dans le diagramme
 En général, il n’est pas recommandé pour naviguer entre les formes et connecteurs sur le diagramme. Il est préférable de parcourir les relations dans le modèle, le déplacement entre les formes et connecteurs uniquement lorsqu’il est nécessaire travailler sur l’apparence du diagramme. Ces méthodes lien connecteurs vers les formes à chaque extrémité :

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 De nombreuses formes sont composites ; elles sont constituées d’une forme parent et une ou plusieurs couches d’enfants. Les formes sont positionnés par rapport à une autre forme sont dits se situer ses *enfants*. Lorsque la forme parente se déplace, les enfants se déplacent avec lui.

 *Enfants relatifs* peut apparaître en dehors de la zone englobante de la forme parent. *Imbriqué* enfants apparaissent strictement l’intérieur des limites du parent.

 Pour obtenir le jeu du haut de formes sur un diagramme, utilisez :

 `Diagram.NestedChildShapes`

 Les classes de l’ancêtre de formes et connecteurs sont :

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Propriétés des formes et connecteurs
 Dans la plupart des cas, il n’est pas nécessaire apporter des modifications explicites aux formes. Lorsque vous avez modifié les éléments de modèle, les règles de « correction » mettre à jour les formes et connecteurs. Pour plus d’informations, consultez [réponse en cours à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md).

 Toutefois, il est utile apporter des modifications explicites aux formes de propriétés qui sont indépendantes des éléments de modèle. Par exemple, vous pouvez modifier ces propriétés :

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Détermine la hauteur et la largeur de la forme.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -position par rapport à la forme parent ou d’un diagramme

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -l’ensemble des stylets et des pinceaux utilisés pour dessiner la forme ou un connecteur

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -rend la forme invisible

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -rend la forme visible après une `Hide()`

###  <a name="merge"></a> Création d’un élément et sa forme

Lorsque vous créez un élément et le liez dans l’arborescence de relations d’incorporation, une forme est automatiquement créée et associée. Cela est effectué par les règles de « correction » qui s’exécutent à la fin de la transaction. Toutefois, la forme s’affiche dans un emplacement automatiquement affecté, et sa forme, de couleur et d’autres fonctionnalités auront des valeurs par défaut. Pour contrôler la façon dont la forme est créée, vous pouvez utiliser la fonction de fusion. Vous devez tout d’abord ajouter les éléments que vous souhaitez ajouter dans un ElementGroup et puis de fusionner le groupe dans le diagramme.

Cette méthode :

-   Définit le nom, si vous avez affecté une propriété en tant que le nom d’élément.

-   Observe les Directives de fusion d’éléments que vous avez spécifié dans la définition DSL.

Cet exemple crée une forme à la position de la souris, lorsque l’utilisateur double-clique sur le diagramme. Dans la définition DSL pour cet exemple, le `FillColor` propriété du `ExampleShape` a été exposé.

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 Si vous fournissez plusieurs formes, définissez leurs positions relatives à l’aide de la `AbsoluteBounds`.

 Vous pouvez également définir la couleur et autres propriétés exposées de connecteurs à l’aide de cette méthode.

### <a name="use-transactions"></a>Utiliser des Transactions
 Formes, des connecteurs et des diagrammes sont des sous-types de <xref:Microsoft.VisualStudio.Modeling.ModelElement> et en direct dans le Store. Vous devez donc les modifier uniquement à l’intérieur d’une transaction. Pour plus d’informations, consultez [Comment : utiliser les Transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Affichage de document et les données de Document
 ![Diagramme de classes des types de diagramme standard](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Partitions de Store
 Lorsqu’un modèle est chargé, le diagramme qui accompagne cet article est chargé en même temps. En règle générale, le modèle est chargé dans Store.DefaultPartition, et le contenu du diagramme est chargé dans une autre Partition. En règle générale, le contenu de chaque partition est chargé et enregistré dans un fichier distinct.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)
- [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)
- [Guide pratique pour utiliser des transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Propagation et réponse aux modifications](../modeling/responding-to-and-propagating-changes.md)
