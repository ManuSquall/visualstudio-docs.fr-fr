---
title: Personnalisation de la fenêtre Propriétés
description: Découvrez comment personnaliser l’apparence et le comportement de la fenêtre Propriétés dans votre langage spécifique à un domaine (DSL) dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e1bd54850264c33c5317a4395f219689a8e8634
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385797"
---
# <a name="customize-the-properties-window"></a>Personnaliser le Fenêtre Propriétés

Vous pouvez personnaliser l’apparence et le comportement de la fenêtre Propriétés dans votre langage spécifique à un domaine (DSL) dans Visual Studio. Dans votre définition DSL, vous définissez des propriétés de domaine sur chaque classe de domaine. Par défaut, lorsque vous sélectionnez une instance de la classe, sur un diagramme ou dans l’Explorateur de modèles, chaque propriété de domaine est listée dans la fenêtre Propriétés. Cela vous permet d’afficher et de modifier les valeurs des propriétés de domaine, même si vous ne les avez pas mappées à des champs de forme sur le diagramme.

## <a name="names-descriptions-and-categories"></a>Noms, descriptions et catégories

**Nom et nom complet**. Dans la définition d’une propriété de domaine, le nom complet de la propriété est le nom qui apparaît au moment de l’exécution dans la fenêtre Propriétés. En revanche, le nom est utilisé lorsque vous écrivez du code de programme pour mettre à jour la propriété. Le nom doit être un nom alphanumérique correct, mais le nom d’affichage peut contenir des espaces.

Lorsque vous définissez le nom d’une propriété dans la définition DSL, son nom d’affichage est automatiquement défini sur une copie du nom. Si vous écrivez un nom en casse Pascal comme « FuelGauge », le nom complet contient automatiquement un espace : « jauge de carburant ». Toutefois, vous pouvez définir le nom d’affichage explicitement sur une autre valeur.

**Description**. La description d’une propriété de domaine apparaît à deux emplacements :

- En bas de la fenêtre Propriétés lorsque l’utilisateur sélectionne la propriété. Vous pouvez l’utiliser pour expliquer à l’utilisateur ce que représente la propriété.

- Dans le code du programme généré. Si vous utilisez les fonctionnalités de la documentation pour extraire la documentation de l’API, celle-ci s’affiche comme description de cette propriété dans l’API.

**Catégorie**. Une catégorie est un titre dans la Fenêtre Propriétés.

## <a name="expose-style-features"></a>Exposer les fonctionnalités de style

Certaines des fonctionnalités dynamiques des éléments graphiques peuvent être représentées ou *exposées* en tant que propriétés de domaine. Une fonctionnalité qui a été exposée de cette manière peut être mise à jour par l’utilisateur et peut être plus facilement mise à jour par le code de programme.

Cliquez avec le bouton droit sur une classe de forme dans la définition DSL, pointez sur **Ajouter exposé**, puis choisissez une fonctionnalité.

Sur les formes, vous pouvez exposer les propriétés **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** et **FillGradientMode** . Sur les connecteurs, vous pouvez exposer les propriétés **Color** `,` **TextColor**, **DashStyle** et **Thickness** . Sur les diagrammes, vous pouvez exposer les propriétés **FillColor** et **TextColor** .

## <a name="forwarding-display-properties-of-related-elements"></a>Transfert : afficher les propriétés des éléments associés

Lorsque l’utilisateur de votre DSL sélectionne un élément dans un modèle, les propriétés de cet élément s’affichent dans la fenêtre Propriétés. Toutefois, vous pouvez également afficher les propriétés des éléments associés spécifiés. Cela est utile si vous avez défini un groupe d’éléments qui fonctionne ensemble. Par exemple, vous pouvez définir un élément principal et un élément de plug-in facultatif. Si l’élément principal est mappé à une forme et que l’autre ne l’est pas, il est utile de voir toutes leurs propriétés comme si elles se trouvaient sur un élément.

Cet effet est appelé *transfert de propriété* et se produit automatiquement dans plusieurs cas. Dans d’autres cas, vous pouvez obtenir le transfert de propriété en définissant un descripteur de type de domaine.

### <a name="default-property-forwarding-cases"></a>Cas de transfert de propriété par défaut

Lorsque l’utilisateur sélectionne une forme ou un connecteur, ou un élément dans l’Explorateur, les propriétés suivantes s’affichent dans la Fenêtre Propriétés :

- Propriétés de domaine qui sont définies sur la classe de domaine de l’élément de modèle, y compris celles qui sont définies dans les classes de base. Une exception est que les propriétés de domaine pour lesquelles vous avez défini peuvent être **explorables** `False` .

- Noms des éléments qui sont liés par des relations qui ont une multiplicité de 0.. 1. Cela offre une méthode pratique pour voir les éléments liés éventuellement, même si vous n’avez pas défini de mappage de connecteur pour la relation.

- Propriétés de domaine de la relation d’incorporation qui cible l’élément. Étant donné que les relations d’incorporation ne sont généralement pas affichées explicitement, cela permet à l’utilisateur de voir ses propriétés.

- Propriétés de domaine définies sur la forme ou le connecteur sélectionné.

### <a name="add-property-forwarding"></a>Ajouter le transfert de propriété

Pour transférer une propriété, vous devez définir un descripteur de type de domaine. Si vous avez une relation de domaine entre deux classes de domaine, vous pouvez utiliser un descripteur de type de domaine pour affecter à une propriété de domaine de la première classe la valeur d’une propriété de domaine dans la deuxième classe de domaine. Par exemple, si vous avez une relation entre une classe de domaine **Book** et une classe de domaine **Author** , vous pouvez utiliser un descripteur de type de domaine pour que la propriété **Name** de l' **auteur** d’un livre apparaisse dans le fenêtre Propriétés lorsque l’utilisateur sélectionne le livre.

> [!NOTE]
> Le transfert de propriété affecte uniquement les Fenêtre Propriétés lorsque l’utilisateur modifie un modèle. Elle ne définit pas une propriété de domaine sur la classe de réception. Si vous souhaitez accéder à la propriété de domaine transféré dans d’autres parties de la définition DSL ou dans le code de programme, vous devez accéder à l’élément de transfert.

La procédure suivante suppose que vous avez créé un DSL. Les premières étapes résument les conditions préalables.

#### <a name="forward-a-property-from-another-element"></a>Transférer une propriété à partir d’un autre élément

1. Créez une [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solution qui contient au moins deux classes qui, dans cet exemple, sont appelées **Book** et **Author**. Il doit y avoir une relation entre le **livre** et l' **auteur**.

    La multiplicité du rôle source (le rôle du côté **livre** ) doit être 0.. 1 ou 1.. 1, de sorte que chaque **livre** ait un **auteur**.

2. Dans l' **Explorateur DSL**, cliquez avec le bouton droit sur la classe de domaine **Book** , puis cliquez sur **Ajouter un nouveau DomainTypeDescriptor**.

    Un nœud nommé **chemins des descripteurs de propriétés personnalisées** apparaît sous le nœud descripteur de **type personnalisé** .

3. Cliquez avec le bouton droit sur le nœud **descripteur de type personnalisé** , puis cliquez sur **Ajouter un nouveau PropertyPath**.

    Un nouveau chemin de propriété apparaît sous le nœud **chemins d’accès des descripteurs de propriétés personnalisées** .

4. Sélectionnez le nouveau chemin d’accès de la propriété, puis dans la fenêtre **Propriétés** , définissez **chemin d’accès à la propriété** sur le chemin d’accès de l’élément de modèle approprié.

    Vous pouvez modifier le chemin d’accès dans une arborescence en cliquant sur la flèche vers le bas à droite de cette propriété. Pour plus d’informations sur les chemins de domaine, consultez [syntaxe du chemin d’accès au domaine](../modeling/domain-path-syntax.md). Une fois que vous l’avez modifiée, le chemin d’accès doit ressembler à **BookReferencesAuthor. Author/ ! Auteur**.

5. **Affectez** la valeur à la propriété **nom** de domaine de l' **auteur**.

6. Définissez le **nom d’affichage** sur le nom de l' **auteur**.

7. Transformez tous les modèles, générez et exécutez le DSL.

8. Dans un diagramme de modèle, créez un livre, un auteur, puis liez-le à l’aide de la relation de référence. Sélectionnez l’élément book, puis dans la Fenêtre Propriétés vous devriez voir nom de l’auteur en plus des propriétés du livre. Modifiez le nom de l’auteur lié, ou liez le livre à un autre auteur, et observez que le nom de l’auteur du livre change.

## <a name="custom-property-editors"></a>Éditeurs de propriétés personnalisées

La fenêtre de propriétés fournit une expérience de modification par défaut appropriée pour le type de chaque propriété de domaine. Par exemple, pour un type énuméré, l’utilisateur voit une liste déroulante, et pour une propriété numérique, l’utilisateur peut entrer des chiffres. Cela est vrai uniquement pour les types intégrés. Si vous spécifiez un type externe, l’utilisateur sera en mesure de voir les valeurs de la propriété, mais pas de la modifier.

Toutefois, vous pouvez spécifier les éditeurs et types suivants :

1. Autre éditeur utilisé avec un type standard. Par exemple, vous pouvez spécifier un éditeur de chemin d’accès de fichier pour une propriété de type chaîne.

2. Un type externe pour la propriété de domaine et un éditeur pour celui-ci.

3. Un éditeur .NET, tel que l’éditeur de chemin de fichier, ou vous pouvez créer votre propre éditeur de propriétés personnalisées.

   Conversion entre un type externe et un type tel que String, qui a un éditeur par défaut.

   Dans un DSL, un *type externe* est tout type qui ne fait pas partie des types simples (tels que booléen ou Int32) ou String.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Définir une propriété de domaine qui a un type externe

1. Dans **Explorateur de solutions**, ajoutez une référence à l’assembly (dll) qui contient le type externe dans le projet **DSL** .

    L’assembly peut être un assembly .NET ou un assembly que vous avez fourni.

2. Ajoutez le type à la liste **types de domaines** , sauf si vous l’avez déjà fait.

   1. Ouvrez DslDefinition. DSL et, dans l' **Explorateur DSL**, cliquez avec le bouton droit sur le nœud racine, puis cliquez sur **Ajouter un nouveau type externe**.

        Une nouvelle entrée apparaît sous le nœud **types de domaine** .

       > [!WARNING]
       > L’élément de menu se trouve sur le nœud racine DSL, et non sur le nœud **types de domaine** .

   2. Définissez le nom et l’espace de noms du nouveau type dans la Fenêtre Propriétés.

3. Ajoutez une propriété de domaine à une classe de domaine de la manière habituelle.

    Dans la Fenêtre Propriétés, sélectionnez le type externe dans la liste déroulante du champ **type** .

   À ce niveau, les utilisateurs peuvent afficher les valeurs de la propriété, mais elles ne peuvent pas la modifier. Les valeurs affichées sont obtenues à partir de la `ToString()` fonction. Vous pouvez écrire du code de programme qui définit la valeur de la propriété, par exemple dans une commande ou une règle.

### <a name="set-a-property-editor"></a>Définir un éditeur de propriétés

Ajoutez un attribut CLR à la propriété de domaine, sous la forme suivante :

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Vous pouvez définir l’attribut sur une propriété à l’aide de l’entrée **attribut personnalisé** dans la fenêtre Propriétés.

Le type de `AnEditor` doit être dérivé du type spécifié dans le deuxième paramètre. Le deuxième paramètre doit avoir la valeur <xref:System.Drawing.Design.UITypeEditor> ou <xref:System.ComponentModel.ComponentEditor> . Pour plus d’informations, consultez <xref:System.ComponentModel.EditorAttribute>.

Vous pouvez spécifier votre propre éditeur ou un éditeur .NET, tel que <xref:System.Windows.Forms.Design.FileNameEditor> ou <xref:System.Drawing.Design.ImageEditor> . Par exemple, utilisez la procédure suivante pour avoir une propriété dans laquelle l’utilisateur peut entrer un nom de fichier.

#### <a name="define-a-file-name-domain-property"></a>Définir un nom de fichier, propriété de domaine

1. Ajoutez une propriété de domaine à une classe de domaine dans votre définition DSL.

2. Sélectionnez la nouvelle propriété. Dans le champ **attribut personnalisé** de la fenêtre Propriétés, entrez l’attribut suivant. Pour entrer cet attribut, cliquez sur les points de suspension **[...]** , puis entrez le nom de l’attribut et les paramètres séparément :

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Laissez le type de la propriété de domaine à sa valeur par défaut **String**.

4. Pour tester l’éditeur, vérifiez que les utilisateurs peuvent ouvrir l’éditeur de noms de fichiers pour modifier votre propriété de domaine.

    1. Appuyez sur CTRL + F5 ou F5. Dans la solution de débogage, ouvrez un fichier de test. Créez un élément de la classe de domaine et sélectionnez-le.

    2. Dans le Fenêtre Propriétés, sélectionnez la propriété de domaine. Le champ valeur affiche des points de suspension **[...]**.

    3. Cliquez sur les points de suspension. Une boîte de dialogue fichier s’affiche. Sélectionnez un fichier et fermez la boîte de dialogue. Le chemin d’accès du fichier est maintenant la valeur de la propriété de domaine.

### <a name="define-your-own-property-editor"></a>Définir votre propre éditeur de propriétés

Vous pouvez définir votre propre éditeur. Vous pouvez le faire pour permettre à l’utilisateur de modifier un type que vous avez défini ou de modifier un type standard d’une façon spéciale. Par exemple, vous pouvez autoriser l’utilisateur à entrer une chaîne qui représente une formule.

Vous définissez un éditeur en écrivant une classe dérivée de <xref:System.Drawing.Design.UITypeEditor> . Votre classe doit remplacer :

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, pour interagir avec l’utilisateur et mettre à jour la valeur de la propriété.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, pour spécifier si votre éditeur doit ouvrir une boîte de dialogue ou fournir un menu déroulant.

Vous pouvez également fournir une représentation graphique de la valeur de la propriété qui sera affichée dans la grille des propriétés. Pour ce faire, substituez `GetPaintValueSupported` et `PaintValue` .  Pour plus d’informations, consultez <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Ajoutez le code dans un fichier de code séparé dans le projet **DSL** .

Exemple :

```csharp
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

Pour utiliser cet éditeur, affectez à l' **attribut personnalisé** d’une propriété de domaine la valeur :

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Pour plus d’informations, consultez <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Fournir une liste déroulante de valeurs

Vous pouvez fournir une liste de valeurs permettant à un utilisateur de choisir.

> [!NOTE]
> Cette technique fournit une liste de valeurs qui peuvent changer au moment de l’exécution. Si vous souhaitez fournir une liste qui ne change pas, envisagez plutôt d’utiliser un type énuméré comme type de votre propriété de domaine.

Pour définir une liste de valeurs standard, vous ajoutez à votre propriété de domaine un attribut CLR qui se présente sous la forme suivante :

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Définissez une classe qui dérive de <xref:System.ComponentModel.TypeConverter>. Ajoutez le code dans un fichier distinct dans le projet **DSL** . Par exemple :

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
