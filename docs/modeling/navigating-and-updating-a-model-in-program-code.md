---
title: "Navigation et la mise à jour d’un modèle dans le Code de programmation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e210b786fab418a84ae6bee70809a68a2dedfa71
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Navigation et mise à jour d'un modèle dans le code de programme
Vous pouvez écrire du code pour créer et supprimer des éléments de modèle, définir leurs propriétés, créer et supprimer les liens entre des éléments. Toutes les modifications doivent être effectuées dans une transaction. Si les éléments peuvent être affichés sur un diagramme, le diagramme doit être « corrigé « automatiquement à la fin de la transaction.  
  
## <a name="in-this-topic"></a>Dans cette rubrique  
 [Un exemple de définition DSL](#example)  
  
 [Navigation dans le modèle](#navigation)  
  
 [L’accès aux informations de classe](#metadata)  
  
 [Effectuer des modifications à l’intérieur d’une Transaction](#transaction)  
  
 [Création d’éléments de modèle](#elements)  
  
 [Création de liens de relation](#links)  
  
 [Suppression d’éléments](#deleteelements)  
  
 [Suppression de liens de relation](#deletelinks)  
  
 [Réorganiser les liens d’une relation](#reorder)  
  
 [Verrous](#locks)  
  
 [Copier et coller](#copy)  
  
 [Navigation et la mise à jour des diagrammes](#diagrams)  
  
 [Navigation entre les formes et des éléments](#views)  
  
 [Propriétés des formes et des connecteurs](#shapeProperties)  
  
 [DocView et DocData](#docdata)  
  
##  <a name="example"></a>Un exemple de définition DSL  
 Il s’agit de la partie principale de DslDefinition.dsl pour les exemples de cette rubrique :  
  
 ![Diagramme de définition DSL &#45; modèle d’arbre généalogique](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Ce modèle est une instance de cette DSL :  
  
 ![Modèle d’arbre généalogique Tudor](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Références et les espaces de noms  
 Pour exécuter le code dans cette rubrique, vous devez référencer :  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 Votre code utilise cet espace de noms :  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 En outre, si vous écrivez le code dans un projet différent de celui dans lequel votre DSL est défini, vous devez importer l’assembly qui est généré par le projet de Dsl.  
  
##  <a name="navigation"></a>Navigation dans le modèle  
  
### <a name="properties"></a>Propriétés  
 Propriétés du domaine que vous définissez dans la définition DSL deviennent les propriétés auxquelles vous pouvez accéder dans le code de programme :  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Si vous souhaitez définir une propriété, vous devez le faire à l’intérieur d’un [transaction](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 En cas de la définition DSL, une propriété **type** est **calculé**, vous ne pouvez pas la définir. Pour plus d’informations, consultez [calculé et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Relations  
 Relations de domaine que vous définissez dans la définition DSL deviennent des paires de propriétés, l’autre sur la classe à chaque extrémité de la relation. Les noms des propriétés s’affichent dans le diagramme de DslDefinition sous forme d’étiquettes sur les rôles au niveau de chaque côté de la relation. En fonction de la multiplicité du rôle, le type de la propriété est la classe à l’autre extrémité de la relation, soit une collection de cette classe.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 Les propriétés à deux extrémités d’une relation sont toujours réciproque. Lorsqu’un lien est créé ou supprimé, les propriétés de rôle sur les deux éléments sont mis à jour. L’expression suivante (qui utilise les extensions de `System.Linq`) est toujours true pour la relation ParentsHaveChildren dans l’exemple :  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Une relation est également représentée par un élément de modèle appelé un *lien*, qui est une instance du type de relation de domaine. Un lien a toujours l’élément d’une source et l’élément d’une cible. L’élément source et l’élément cible peuvent être le même.  
  
 Vous pouvez accéder à un lien et ses propriétés :  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 Par défaut, pas plus d’une instance d’une relation est autorisée à lier n’importe quelle paire d’éléments de modèle. Mais si, dans la définition DSL, le `Allow Duplicates` indicateur a la valeur true pour la relation, puis il peut y avoir plusieurs liaisons, et vous devez utiliser `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 Il existe également d’autres méthodes pour accéder à des liens. Exemple :  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Rôles masqués.** Si, dans la définition DSL, **est la propriété générée** est **false** pour un rôle particulier, puis aucune propriété n’est générée qui correspond à ce rôle. Toutefois, vous pouvez toujours accéder aux liens et parcourir les liens à l’aide des méthodes de la relation :  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 L’exemple le plus fréquemment utilisée est le <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relation, un élément de modèle est liée à la forme qui l’affiche dans un diagramme :  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>Le répertoire de l’élément  
 Vous pouvez accéder à tous les éléments dans le magasin à l’aide de l’annuaire de l’élément :  
  
 `store.ElementDirectory.AllElements`  
  
 Il existe également des méthodes pour la recherche d’éléments, tels que les éléments suivants :  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="metadata"></a>L’accès aux informations de classe  
 Vous pouvez obtenir plus d’informations sur les classes, les relations et les autres aspects de la définition DSL. Exemple :  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 Les classes de l’ancêtre d’éléments de modèle sont les suivantes :  
  
-   ModelElement - tous les éléments et les relations sont ModelElements  
  
-   ElementLink - toutes les relations sont ElementLinks  
  
##  <a name="transaction"></a>Effectuer des modifications à l’intérieur d’une Transaction  
 Chaque fois que votre code de programme change rien dans le magasin, il doit le faire à l’intérieur d’une transaction. Cela s’applique à tous les éléments de modèle, des relations, des formes, des diagrammes et leurs propriétés. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Modeling.Transaction>.  
  
 La méthode la plus commode de gérer une transaction est un `using` instruction entre dans un `try...catch` instruction :  
  
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
  
 Vous pouvez effectuer n’importe quel nombre de modifications à l’intérieur d’une transaction. Vous pouvez ouvrir les nouvelles transactions à l’intérieur d’une transaction active.  
  
 Pour conserver vos modifications, vous devez `Commit` la transaction avant sa suppression. Si une exception se produit qui n’est pas interceptée à l’intérieur de la transaction, le magasin réinitialisera à son état avant les modifications.  
  
##  <a name="elements"></a>Création d’éléments de modèle  
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
  
-   Créer le nouvel élément dans une partition spécifique de la banque. Pour les éléments de modèle et des relations, mais pas les formes, il s’agit généralement de la partition par défaut.  
  
-   Rendre la cible d’une relation d’incorporation. Dans la DslDefinition de cet exemple, chaque personne doit être la cible de relation FamilyTreeHasPeople d’incorporation. Pour ce faire, nous pouvons définir la propriété du rôle FamilyTreeModel de l’objet de la personne, ou ajoutez cette personne à la propriété du rôle de personnes de l’objet FamilyTreeModel.  
  
-   Définir les propriétés d’un nouvel élément, en particulier la propriété pour laquelle `IsName` a la valeur true dans la DslDefinition. Cet indicateur marque la propriété qui sert à identifier l’élément de façon unique au sein de son propriétaire. Dans ce cas, la propriété de nom a cet indicateur.  
  
-   La définition DSL de cette DSL doit avoir été chargée dans le magasin. Si vous écrivez une extension comme une commande de menu, cela sera généralement déjà être true. Dans d’autres cas, vous pouvez explicitement charger le modèle dans le magasin, ou utiliser <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> à le charger. Pour plus d’informations, consultez [Comment : ouvrir un modèle à partir du fichier de Code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Lorsque vous créez un élément de cette façon, une forme est automatiquement créée (si la DSL comporte un diagramme). Il s’affiche dans un emplacement automatiquement affecté, avec la forme par défaut, la couleur et autres fonctionnalités. Si vous voulez contrôler comment et où la forme associée, consultez [création d’un élément et sa forme](#merge).  
  
##  <a name="links"></a>Création de liens de relation  
 Il existe deux relations définies dans l’exemple de définition DSL. Chaque relation définit une *propriété role* sur la classe à chaque extrémité de la relation.  
  
 Il existe trois façons dans laquelle vous pouvez créer une instance d’une relation. Chacune de ces trois méthodes a le même effet :  
  
-   Définissez la propriété de l’acteur de rôle source. Exemple :  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   Définissez la propriété de l’acteur de rôle cible. Exemple :  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         La multiplicité de ce rôle est `1..1`, donc nous affectons la valeur.  
  
    -   `henry.Children.Add(edward);`  
  
         La multiplicité de ce rôle est `0..*`, donc nous ajouter à la collection.  
  
-   Construire une instance de la relation de façon explicite. Exemple :  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 La dernière méthode est utile si vous souhaitez définir des propriétés sur la relation elle-même.  
  
 Lorsque vous créez un élément de cette façon, un connecteur sur le diagramme est automatiquement créé, mais il a une forme par défaut, la couleur et autres fonctionnalités. Pour contrôler la façon dont le connecteur associé est créé, consultez [création d’un élément et sa forme](#merge).  
  
##  <a name="deleteelements"></a>Suppression d’éléments  
 Supprimer un élément en appelant `Delete()`:  
  
 `henry.Delete();`  
  
 Cette opération supprimera également :  
  
-   Relation des liens vers et à partir de l’élément. Par exemple, `edward.Parents` ne contient plus de `henry`.  
  
-   Éléments sur les rôles pour lesquels le `PropagatesDelete` indicateur a la valeur true. Par exemple, la forme qui affiche l’élément sera supprimée.  
  
 Par défaut, chaque relation incorporation a `PropagatesDelete` true au niveau du rôle cible. Suppression `henry` ne supprime pas le `familyTree`, mais `familyTree.Delete()` supprime tous les `Persons`. Pour plus d’informations, consultez [comportement de suppression de personnalisation](../modeling/customizing-deletion-behavior.md).  
  
 Par défaut, `PropagatesDelete` n’est pas vrai pour les rôles de relations de référence.  
  
 Vous pouvez provoquer les règles de suppression omettre propagations spécifiques lorsque vous supprimez un objet. Cela est utile si vous remplacez un élément d’un autre. Vous fournissez le GUID d’un ou plusieurs rôles pour lesquels la suppression ne doit pas être propagée. Le GUID peut être obtenu à partir de la classe de relation :  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (Cet exemple particulier n’a aucun effet, car `PropagatesDelete` est `false` pour les rôles de la `ParentsHaveChildren` relation.)  
  
 Dans certains cas, la suppression est interdite par l’existence d’un verrou, sur l’élément ou sur un élément qui serait supprimé par propagation. Vous pouvez utiliser `element.CanDelete()` pour vérifier si l’élément peut être supprimé.  
  
##  <a name="deletelinks"></a>Suppression de liens de relation  
 Vous pouvez supprimer un lien de relation en supprimant un élément d’une propriété de rôle :  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 Vous pouvez également supprimer le lien explicitement :  
  
 `edwardHenryLink.Delete();`  
  
 Ces trois méthodes ont toutes le même effet. Vous devez uniquement utiliser un d’eux.  
  
 Si le rôle a une multiplicité de valeur 0.. 1 ou 1.. 1, vous pouvez le définir sur `null`, ou à une autre valeur :  
  
 `edward.FamilyTreeModel = null;`ou :  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="reorder"></a>Réorganisation sur les liens d’une relation  
 Les liens d’une relation particulière provenant ou ciblée sur un élément de modèle particulier ont un ordre spécifique. Ils apparaissent dans l’ordre dans lequel ils ont été ajoutés. Par exemple, cette instruction donne toujours les enfants dans le même ordre :  
  
 `foreach (Person child in henry.Children) ...`  
  
 Vous pouvez modifier l’ordre des liens :  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="locks"></a>Verrous  
 Un verrou peuvent empêcher vos modifications. Verrous peuvent être définies sur le magasin pour des éléments individuels et sur les partitions. Si l’une de ces niveaux possède un verrou qui empêche le type de modification que vous souhaitez effectuer, une exception peut être levée lorsque vous essayez de vous. Vous pouvez découvrir si les verrous sont définis à l’aide d’élément. GetLocks(), qui est une méthode d’extension qui est définie dans l’espace de noms <xref:Microsoft.VisualStudio.Modeling.Immutability>.  
  
 Pour plus d’informations, consultez [définition d’une stratégie de verrouillage pour créer des Segments en lecture seule](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="copy"></a>Copier et coller  
 Vous pouvez copier des éléments ou des groupes d’éléments à un <xref:System.Windows.Forms.IDataObject>:  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Les éléments sont stockés en tant qu’un groupe d’éléments sérialisés.  
  
 Vous pouvez fusionner les éléments d’une interface IDataObject dans un modèle :  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`peut accepter soit un `PresentationElement` ou `ModelElement`. Si vous lui donnez un `PresentationElement`, vous pouvez également spécifier une position sur le schéma cible en tant que troisième paramètre.  
  
##  <a name="diagrams"></a>Navigation et la mise à jour des diagrammes  
 Dans une DSL, l’élément de modèle de domaine, qui représente un concept telles que la personne ou une chanson, est distincte de l’élément de forme, qui représente ce que vous voyez sur le diagramme. L’élément de modèle de domaine stocke les propriétés importantes et les relations des concepts. L’élément forme stocke la taille, la position et la couleur de la vue de l’objet sur le diagramme et la disposition de ses composants.  
  
### <a name="presentation-elements"></a>Éléments de présentation  
 ![Diagramme de classes des types de forme et élément de base](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 Dans votre définition DSL, chaque élément que vous spécifiez crée une classe qui est dérivée d’une des classes standards suivantes.  
  
|Type d’élément|Classe de base|  
|---------------------|----------------|  
|Classe de domaine|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Relation de domaine|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Forme|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Connecteur|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Diagramme|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Un élément sur un diagramme représente généralement un élément de modèle. En général (mais pas toujours), un <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> représente une instance de classe de domaine et un <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> représente une instance de relation de domaine. Le <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relation lie une forme de nœud ou un lien vers l’élément de modèle qu’il représente.  
  
 Chaque forme de nœud ou un lien appartient à un diagramme. Une forme de lien binaire connecte deux formes de nœud.  
  
 Formes peuvent avoir des formes enfants dans les deux jeux. Une forme dans le `NestedChildShapes` jeu se limite à la zone englobante de son parent. Une forme dans le `RelativeChildShapes` liste peut apparaître en dehors ou partiellement en dehors des limites du parent - par exemple une étiquette ou un port. Un diagramme n’a aucun `RelativeChildShapes` et aucun `Parent`.  
  
###  <a name="views"></a>Navigation entre les formes et des éléments  
 Les éléments de modèle de domaine et des éléments de forme sont liées par le <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relation.  
  
```csharp  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 La même relation lie des relations aux connecteurs du diagramme :  
  
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
  
### <a name="navigating-around-the-diagram"></a>Naviguer dans le diagramme  
 En règle générale, il n’est pas conseillé pour naviguer entre les formes et connecteurs du diagramme. Il est préférable de parcourir les relations dans le modèle, le déplacement entre les formes et connecteurs uniquement lorsqu’il est nécessaire travailler sur l’apparence du diagramme. Ces méthodes lier des connecteurs vers les formes à chaque extrémité :  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 De nombreuses formes sont composites ; elles sont constituées d’une forme parent et une ou plusieurs couches d’enfants. Les formes sont positionnés par rapport à une autre forme sont dits son *enfants*. Lorsque la forme parent se déplace, les enfants se déplacent avec lui.  
  
 *Les enfants relatifs* peut apparaître en dehors de la zone englobante de la forme parente. *Imbriqué* enfants apparaissent uniquement dans les limites du parent.  
  
 Pour obtenir le jeu du haut des formes sur un diagramme, utilisez :  
  
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
  
###  <a name="shapeProperties"></a>Propriétés des formes et des connecteurs  
 Dans la plupart des cas, il n’est pas nécessaire apporter des modifications explicites aux formes. Lorsque vous avez modifié les éléments de modèle, les règles de « correction du » mettre à jour les formes et connecteurs. Pour plus d’informations, consultez [réponse aux et propager les modifications](../modeling/responding-to-and-propagating-changes.md).  
  
 Toutefois, il est utile apporter des modifications explicites aux formes dans les propriétés qui sont indépendantes des éléments de modèle. Par exemple, vous pouvez modifier ces propriétés :  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-Détermine la hauteur et la largeur de la forme.  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-position par rapport à la forme parente ou le schéma  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-l’ensemble des stylets et pinceaux utilisé pour dessiner la forme ou un connecteur  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-rend la forme invisible  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-Affiche la forme après une`Hide()`  
  
###  <a name="merge"></a>Création d’un élément et sa forme  
 Lorsque vous créez un élément et la relier dans l’arborescence de l’incorporation des relations, une forme est automatiquement créée et associée. Cela est effectué par les règles de « correction » qui s’exécutent à la fin de la transaction. Toutefois, la forme apparaît dans un emplacement affecté automatiquement et sa forme, de couleur et d’autres fonctionnalités auront des valeurs par défaut. Pour contrôler la façon dont la forme est créée, vous pouvez utiliser la fonction de fusion. Vous devez d’abord ajouter les éléments que vous souhaitez ajouter dans un ElementGroup et puis de fusionner le groupe dans le diagramme.  
  
 Cette méthode :  
  
-   Définit le nom, si vous avez attribué une propriété en tant que nom de l’élément.  
  
-   Observe toutes les Directives fusionner l’élément que vous avez spécifié dans la définition DSL.  
  
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
  
 Si vous fournissez plusieurs formes, définir leurs positions relatives à l’aide de la `AbsoluteBounds`.  
  
 Vous pouvez également définir la couleur et autres propriétés exposées des connecteurs à l’aide de cette méthode.  
  
### <a name="use-transactions"></a>Utiliser des Transactions  
 Formes, les connecteurs et les diagrammes sont des sous-types de <xref:Microsoft.VisualStudio.Modeling.ModelElement> et actives dans le magasin. Vous devez donc modifier leur uniquement à l’intérieur d’une transaction. Pour plus d’informations, consultez [Comment : utiliser les Transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="docdata"></a>Affichage du document et les données du Document  
 ![Diagramme de classes des types de diagramme standard](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Stocker les Partitions  
 Lorsqu’un modèle est chargé, le diagramme qui l’accompagne est chargé en même temps. En règle générale, le modèle est chargé dans Store.DefaultPartition, et le contenu de schéma est chargé dans une autre Partition. En règle générale, le contenu de chaque partition est chargé et enregistré dans un fichier séparé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)   
 [Génération de Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Comment : utiliser des Transactions pour mettre à jour le modèle](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Propagation et réponse aux modifications](../modeling/responding-to-and-propagating-changes.md)
