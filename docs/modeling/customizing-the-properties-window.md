---
title: Personnalisation de la fenêtre Propriétés
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7020d3f49d5a693d2b64891c089138be4c073115
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953990"
---
# <a name="customizing-the-properties-window"></a>Personnalisation de la fenêtre Propriétés
Vous pouvez personnaliser l’apparence et le comportement de la fenêtre Propriétés dans votre langage spécifique à un domaine (DSL) dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans votre définition DSL, vous définissez des propriétés de domaine sur chaque classe de domaine. Par défaut, lorsque vous sélectionnez une instance de la classe, sur un diagramme ou dans l’Explorateur de modèles, chaque propriété de domaine est répertoriée dans la fenêtre Propriétés. Cela vous permet afficher et modifier les valeurs des propriétés de domaine, même si vous n'avez pas mappé aux champs de forme sur le diagramme.

## <a name="names-descriptions-and-categories"></a>Noms, Descriptions et des catégories
 **Nom et le nom d’affichage**. Dans la définition d’une propriété de domaine, le nom complet de la propriété est le nom qui apparaît lors de l’exécution dans la fenêtre Propriétés. En revanche, le nom est utilisé lorsque vous écrivez du code de programme pour mettre à jour la propriété. Le nom doit être un nom alphanumérique CLR correct, mais le nom d’affichage peut contenir des espaces.

 Lorsque vous définissez le nom d’une propriété dans la définition DSL, son nom complet est automatiquement définie à une copie du nom. Si vous écrivez un nom de casse Pascal tels que « FuelGauge », le nom d’affichage contiennent un espace : « Consommation ». Toutefois, vous pouvez définir explicitement le nom complet à une autre valeur.

 **Description**. La Description d’une propriété de domaine s’affiche à deux endroits :

-   Dans la partie inférieure de la fenêtre Propriétés lorsque l’utilisateur sélectionne la propriété. Vous pouvez l’utiliser pour expliquer à l’utilisateur, ce qui représente la propriété.

-   Dans le code de programme généré. Si vous utilisez les fonctionnalités de documentation pour extraire la documentation de l’API, il apparaît comme la description de cette propriété dans l’API.

 **Category**. Une catégorie est un titre dans la fenêtre Propriétés.

## <a name="exposing-style-features"></a>Exposition de fonctionnalités de Style
 Certaines des fonctionnalités dynamiques d’éléments de graphiques peuvent être représentés ou *exposées* en tant que propriétés de domaine. Une fonctionnalité qui a été exposée de cette manière peut être mis à jour par l’utilisateur et peuvent facilement être mis à jour par du code de programme.

 Une classe de la forme de définition DSL d’avec le bouton droit, pointez sur **ajouter exposées**, puis choisissez une fonctionnalité.

 Sur les formes, vous pouvez exposer le **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** et **FillGradientMode** propriétés. Sur les connecteurs, vous pouvez exposer le **couleur**`,`**TextColor**, **DashStyle**, et **épaisseur** propriétés. Sur les diagrammes, vous pouvez exposer le **FillColor** et **TextColor** propriétés.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Transfert : Affichage des propriétés d’éléments connexes
 Lorsque l’utilisateur de votre DSL sélectionne un élément dans un modèle, les propriétés de l’élément sont affichées dans la fenêtre Propriétés. Toutefois, vous pouvez également afficher les propriétés d’éléments connexes spécifiés. Cela est utile si vous avez défini un groupe d’éléments qui fonctionne ensemble. Par exemple, vous pouvez définir un principal et un élément facultatif du plug-in. Si l’élément principal est mappé à une forme et l’autre ne l’est pas, il est utile de consulter toutes leurs propriétés comme s’ils étaient sur un seul élément.

 Cet effet se nomme *transfert de propriété*, et il se produit automatiquement dans plusieurs cas. Dans d’autres cas, vous pouvez obtenir la propriété de transfert en définissant un descripteur de type de domaine.

### <a name="default-property-forwarding-cases"></a>Cas de transfert de propriété par défaut
 Lorsque l’utilisateur sélectionne une forme ou connecteur ou un élément dans l’Explorateur, les propriétés suivantes sont affichent dans la fenêtre Propriétés :

-   Les propriétés du domaine qui sont définies sur la classe de domaine de l’élément de modèle, y compris ceux qui sont définis dans les classes de base. Une exception est propriétés du domaine pour lequel vous avez défini **est consultable** à `False`.

-   Les noms des éléments qui sont liés par des relations qui ont une multiplicité de 0.. 1. Cela fournit une méthode pratique de voir éventuellement liée à des éléments, même si vous n’avez pas défini un mappage de connecteur pour la relation.

-   Propriétés du domaine de la relation d’incorporation qui cible l’élément. Étant donné que l’incorporation de relations ne sont généralement pas affichées explicitement, cela permet à l’utilisateur voir leurs propriétés.

-   Propriétés du domaine qui sont définies sur la forme sélectionnée ou d’un connecteur.

### <a name="adding-property-forwarding"></a>Ajout de transfert de propriété
 Pour transférer une propriété, vous définissez un descripteur de type de domaine. Si vous disposez d’une relation de domaine entre deux classes de domaine, vous pouvez utiliser un descripteur de type de domaine pour définir une propriété de domaine dans la première classe à la valeur d’une propriété de domaine dans la deuxième classe de domaine. Par exemple, si vous disposez d’une relation entre un **carnet de** classe de domaine et un **auteur** classe de domaine, vous pouvez utiliser un descripteur de type de domaine pour rendre le **nom** propriété d’un L’ouvrage **auteur** s’affichent dans la fenêtre Propriétés lorsque l’utilisateur sélectionne la loi.

> [!NOTE]
>  Transfert de propriété affecte uniquement la fenêtre Propriétés lorsque l’utilisateur modifie un modèle. Il ne définit pas une propriété de domaine sur la classe réceptrice. Si vous souhaitez accéder à la propriété de domaine transféré dans d’autres parties de la définition DSL ou dans le code de programme, vous devez accéder à l’élément de transfert.

 La procédure suivante suppose que vous avez créé une DSL. La première procédure résument les conditions préalables.

##### <a name="to-forward-a-property-from-another-element"></a>Pour transférer une propriété à partir d’un autre élément

1.  Créer un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solution qui contient au moins deux classes, appelées dans cet exemple **Book** et **auteur**. Il doit y avoir une relation de chaque type entre **Book** et **auteur**.

     La multiplicité du rôle source (le rôle à la **Book** côté) doit être de valeur 0.. 1 ou 1 de.. 1, afin que chaque **carnet de** a un **auteur**.

2.  Dans **Explorateur DSL**, avec le bouton droit le **Book** classe de domaine, puis cliquez sur **ajouter un nouveau DomainTypeDescriptor**.

     Un nœud nommé **chemins d’accès de descripteurs de propriété personnalisée** apparaît sous le **descripteur de Type personnalisé** nœud.

3.  Avec le bouton droit le **descripteur de Type personnalisé** nœud, puis cliquez sur **ajouter un nouveau PropertyPath**.

     Un nouveau chemin d’accès de propriété apparaît sous la **chemins d’accès de descripteurs de propriété personnalisée** nœud.

4.  Sélectionnez le nouveau chemin de propriété, puis, dans le **propriétés** , configurez **chemin d’accès à la propriété** pour le chemin d’accès de l’élément de modèle approprié.

     Vous pouvez modifier le chemin d’accès dans une arborescence en cliquant sur la flèche vers le bas à droite de cette propriété. Pour plus d’informations sur les chemins d’accès du domaine, consultez [la syntaxe du chemin d’accès au domaine](../modeling/domain-path-syntax.md). Lorsque vous l’avez modifié, le chemin d’accès doit ressembler à **BookReferencesAuthor.Author/ ! Auteur**.

5.  Définissez **propriété** à la **nom** propriété de domaine de **auteur**.

6.  Définissez **nom d’affichage** à **créer nom**.

7.  Transformer tous les modèles, générer et exécuter la DSL.

8.  Dans un diagramme de modèle, créer un livre, un auteur et les lier à l’aide de la relation de référence. Sélectionnez l’élément « book » et dans la fenêtre Propriétés vous devez voir le nom de l’auteur en plus des propriétés de l’annuaire. Modifier le nom de l’auteur lié, ou lier le livre à un autre auteur et observez que le nom de l’auteur du livre change.

## <a name="custom-property-editors"></a>Éditeurs de propriétés personnalisées
 La fenêtre de propriété fournit une valeur par défaut appropriée éditeur choisi pour le type de chaque propriété de domaine. Par exemple, pour un type énuméré, l’utilisateur voit une liste déroulante, et pour une propriété numérique, l’utilisateur peut entrer des chiffres. Cela vaut uniquement pour les types intégrés. Si vous spécifiez un type externe, l’utilisateur sera en mesure d’afficher les valeurs de la propriété, mais pas le modifier.

 Toutefois, vous pouvez spécifier les éditeurs et les types suivants :

1.  Un autre éditeur qui est utilisé avec un type standard. Par exemple, vous pouvez spécifier un éditeur du chemin d’accès de fichier pour une propriété de chaîne.

2.  Un type externe pour la propriété de domaine et un éditeur pour celle-ci.

3.  Un éditeur .NET tels que l’Éditeur du chemin d’accès au fichier, ou vous pouvez créer votre propre propriété personnalisée éditeur.

     Une conversion entre un type externe et un type de chaîne, qui fournit un éditeur de valeur par défaut.

 Dans une DSL, un *type externe* correspond à tout type qui n’est pas un des types simples (par exemple, la valeur booléenne ou Int32) ou chaîne.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Pour définir une propriété de domaine qui possède un type externe

1.  Dans **l’Explorateur de solutions**, ajoutez une référence à l’assembly (DLL) qui contient le type externe, dans le **Dsl** projet.

     L’assembly peut être un assembly .NET ou un assembly fourni.

2.  Ajouter le type à la **Types de domaine** liste, sauf si vous avez déjà fait.

    1.  Ouvrez DslDefinition.dsl et dans **Explorateur DSL**, cliquez sur le nœud racine, puis cliquez sur **ajouter un nouveau Type externe**.

         Une nouvelle entrée apparaît sous le **Types de domaine** nœud.

        > [!WARNING]
        >  L’élément de menu n’est pas sur le nœud racine DSL, le **Types de domaine** nœud.

    2.  Dans la fenêtre Propriétés, définissez le nom et l’espace de noms du nouveau type.

3.  Ajouter une propriété de domaine à une classe de domaine de la manière habituelle.

     Dans la fenêtre Propriétés, sélectionnez le type externe dans la liste déroulante de la **Type** champ.

 À ce stade, les utilisateurs peuvent afficher les valeurs de la propriété, mais ils ne peuvent pas le modifier. Les valeurs affichées sont obtenues à partir de la `ToString()` (fonction). Vous pouvez écrire du code de programme qui définit la valeur de la propriété, par exemple dans une commande ou une règle.

### <a name="setting-a-property-editor"></a>Définition d’un éditeur de propriétés
 Ajoutez un attribut CLR à la propriété de domaine, sous la forme suivante :

```
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]

```

 Vous pouvez définir l’attribut sur une propriété à l’aide de la **attribut personnalisé** entrée dans la fenêtre Propriétés.

 Le type de `AnEditor` doit être dérivé du type spécifié dans le deuxième paramètre. Le deuxième paramètre doit être <xref:System.Drawing.Design.UITypeEditor> ou <xref:System.ComponentModel.ComponentEditor>. Pour plus d'informations, consultez <xref:System.ComponentModel.EditorAttribute>.

 Vous pouvez spécifier votre propre éditeur, ou un éditeur fourni dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], tel que <xref:System.Windows.Forms.Design.FileNameEditor> ou <xref:System.Drawing.Design.ImageEditor>. Par exemple, utilisez la procédure suivante pour disposer d’une propriété dans lequel l’utilisateur peut entrer un nom de fichier.

##### <a name="to-define-a-file-name-domain-property"></a>Pour définir une propriété de domaine de nom de fichier

1.  Ajouter une propriété de domaine à une classe de domaine dans votre définition DSL.

2.  Sélectionnez la nouvelle propriété. Dans le **attribut personnalisé** dans la fenêtre Propriétés, entrez l’attribut suivant. Pour entrer cet attribut, cliquez sur le bouton de sélection **[...]**  , puis entrez le nom d’attribut et les paramètres séparément :

    ```
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  Conservez le Type de la propriété de domaine par défaut **chaîne**.

4.  Pour tester l’éditeur, vérifiez que les utilisateurs peuvent ouvrir l’éditeur de nom de fichier pour modifier votre propriété de domaine.

    1.  Appuyez sur CTRL + F5 ou F5. Dans la solution de débogage, ouvrez un fichier de test. Créer un élément de la classe de domaine et sélectionnez-le.

    2.  Dans la fenêtre Propriétés, sélectionnez la propriété de domaine. Le champ de valeur affiche les points de suspension **[...]** .

    3.  Cliquez sur le bouton de sélection. Une boîte de dialogue s’affiche. Sélectionnez un fichier et fermez la boîte de dialogue. Le chemin d’accès est désormais la valeur de la propriété de domaine.

### <a name="defining-your-own-property-editor"></a>Définir votre propre éditeur de propriétés
 Vous pouvez définir votre propre éditeur. Cette tâche est nécessaire pour autoriser l’utilisateur à modifier un type que vous avez définies, ou pour modifier un type standard d’une façon particulière. Par exemple, vous pouvez autoriser l’utilisateur à entrer une chaîne qui représente une formule.

 Vous définissez un éditeur en écrivant une classe qui est dérivée de <xref:System.Drawing.Design.UITypeEditor>. Votre classe doit substituer :

-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, pour interagir avec l’utilisateur et mettre à jour la valeur de propriété.

-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, pour spécifier que votre éditeur ouvrir une boîte de dialogue ou fournir un menu déroulant.

 Vous pouvez également fournir une représentation graphique de la valeur de propriété qui s’affichera dans la grille des propriétés. Pour ce faire, vous devez substituer `GetPaintValueSupported`, et `PaintValue`.  Pour plus d'informations, consultez <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Ajoutez le code dans un fichier de code séparé dans le **Dsl** projet.

 Par exemple :

```
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}

```

 Pour utiliser cet éditeur, définissez la **attribut personnalisé** d’une propriété de domaine à :

```
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]

```

 Pour plus d'informations, consultez <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>En fournissant une liste déroulante de valeurs
 Vous pouvez fournir une liste de valeurs pour un utilisateur à sélectionner.

> [!NOTE]
>  Cette technique fournit une liste de valeurs qui peuvent changer pendant l’exécution. Si vous souhaitez fournir une liste ne change pas, pensez à la place à l’aide d’un type énuméré en tant que le type de propriété de votre domaine.

 Pour définir une liste de valeurs standards, vous ajoutez à votre propriété de domaine un attribut CLR qui a la forme suivante :

```
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]

```

 Définissez une classe qui dérive de <xref:System.ComponentModel.TypeConverter>. Ajoutez le code dans un fichier distinct dans le **Dsl** projet. Par exemple :

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}

```

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)