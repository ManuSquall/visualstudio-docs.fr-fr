---
title: "Personnalisation de la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, Propriétés (fenêtre)"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Personnalisation de la fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez personnaliser l'apparence et le comportement de la fenêtre de propriétés dans votre langage \(DSL\) spécifique au domaine dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Dans la définition de langage spécifique à un domaine, vous définissez les propriétés de domaine sur chaque classe de domaine.  Par défaut, lorsque vous sélectionnez une instance de la classe, sur un diagramme ou dans l'explorateur de modèles, chaque propriété de domaine est répertorié dans la fenêtre de propriétés.  Cela vous permet de visualiser et modifier les valeurs des propriétés de domaine, même si vous ne les avez pas mappées pour personnaliser les champs sur le diagramme.  
  
## noms, descriptions, et catégories  
 **nom et nom complet**.  Dans votre définition d'une propriété de domaine, le nom complet de la propriété est le nom qui apparaît au moment de l'exécution dans la fenêtre de propriétés.  En revanche, le nom est utilisé lorsque vous écrivez du code de programme pour mettre à jour la propriété.  Le nom doit être un nom alphanumérique correct du CLR, mais le nom complet peut contenir d'espaces.  
  
 Lorsque vous définissez le nom d'une propriété dans la définition DÉSOLÉ, son nom complet est automatiquement à une copie du nom.  Si vous entrez un nom la conversion par Pascal tel que « FuelGauge », le nom complet contiendra automatiquement un espace : « Jauge de carburant ».  Toutefois, vous pouvez définir le nom complet explicitement à une autre valeur.  
  
 **Description**.  La description d'une propriété de domaine s'affiche dans deux emplacements :  
  
-   En bas de la fenêtre de propriétés lorsque l'utilisateur sélectionne la propriété.  Vous pouvez l'utiliser pour expliquer à l'utilisateur que représente la propriété.  
  
-   Dans le code de programme généré.  Si vous utilisez les fonctions de documentation pour récupérer la documentation API, elle apparaîtra comme une description de cette propriété dans l'API.  
  
 **Catégorie**.  une catégorie est un titre dans la fenêtre Propriétés.  
  
## exposer des fonctionnalités de style  
 Certaines fonctionnalités dynamiques des éléments graphiques peuvent être représentées ou *exposées* comme propriétés de domaine.  Une fonctionnalité qui était exposée par cette application peut être mise à jour par l'utilisateur et peut être plus facilement mise à jour par le code du programme.  
  
 Cliquez avec le bouton droit sur une classe de forme dans la définition DÉSOLÉ, pointez sur **ajoutez exposé**, puis choisissez une fonctionnalité.  
  
 Sur les formes vous pouvez exposer **couleur de remplissage**, les propriétés d' **OutlineColor**, de **TextColor**, d' **OutlineDashStyle**, d' **OutlineThickness** et de **FillGradientMode** .  Sur les connecteurs vous pouvez exposer **Couleur**`,`**TextColor**, **DashStyle**, les propriétés et d' **épaisseur** .  Sur les diagrammes vous pouvez exposer **couleur de remplissage** et les propriétés de **TextColor** .  
  
## transférer : Affichage des propriétés d'éléments associés  
 Lorsque l'utilisateur de votre DÉSOLÉ sélectionne un élément dans un modèle, les propriétés de cet élément sont affichées dans la fenêtre de propriétés.  Toutefois, vous pouvez également afficher les propriétés d'éléments associés spécifiés.  Cela est utile si vous avez défini un groupe d'éléments qui travaille ensemble.  Par exemple, vous pouvez définir un élément principal et un élément du plug\-in facultatif.  Si l'élément head est mappé à une forme et l'autre ne l'est pas, il est utile de consulter toutes leurs propriétés comme si elles étaient sur un élément.  
  
 L'effet est nommé *propriété en transférant*, et il se produit automatiquement dans plusieurs cas.  Dans d'autres cas, vous pouvez effectuer la propriété en transférant en définissant un descripteur de type de domaine.  
  
### Propriété par défaut en transférant les cas  
 Lorsque l'utilisateur sélectionne une forme ou un connecteur, ou un élément dans l'explorateur, les propriétés suivantes sont affichées dans la fenêtre Propriétés :  
  
-   Les propriétés de domaine qui sont définies dans la classe de domaine de l'élément de modèle, y compris ceux qui sont définis dans les classes de base.  une exception est des propriétés de domaine pour lesquelles vous avez défini **Peut être exploré** à `False`.  
  
-   Les noms des éléments liés via les relations qui ont une multiplicité de 0..1.  Cela fournit une méthode pratique pour voir les éléments éventuellement liés, même si vous n'avez pas défini de mappage de connecteur de la relation.  
  
-   propriétés de domaine de la relation d'incorporation qui cible l'élément.  Comme incorporant des relations généralement ne sont pas affichés explicitement, cela permet à l'utilisateur de voir leurs propriétés.  
  
-   propriétés de domaine qui sont définies sur la forme ou le connecteur sélectionnée.  
  
### Transférer de propriété d'addition  
 pour transférer une propriété, vous définissez un descripteur de type de domaine.  Si vous avez une relation de domaine entre deux classes, vous pouvez utiliser un descripteur de type de domaine pour définir une propriété de domaine dans la première classe à la valeur d'une propriété de domaine dans la deuxième classe de domaine.  Par exemple, si vous avez une relation entre une classe de domaine de livre et une classe de domaine d'auteur, vous pouvez utiliser un descripteur de type de domaine pour que la propriété Name de l'auteur d'un livre apparaître dans la fenêtre Propriétés lorsque l'utilisateur sélectionne le livre.  
  
> [!NOTE]
>  Propriété en transférant affecte uniquement la fenêtre Propriétés lorsque l'utilisateur modifie un modèle.  Il ne définit pas une propriété de domaine sur la classe réceptrice.  Si vous souhaitez accéder à la propriété de domaine transférées dans d'autres parties de la définition DÉSOLÉ ou dans le code de programme, vous devez accéder à l'élément de migration.  
  
 La procédure suivante suppose que vous avez créé un langage spécifique à un domaine.  les étapes premières résument les composants requis.  
  
##### pour transférer une propriété d'un autre élément  
  
1.  Créez une solution de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] qui contient au moins deux classes qui, dans cet exemple sont appelées livre et auteur.  Il doit y a une relation de type entre le livre et l'auteur.  
  
     La multiplicité du rôle de source \(rôle sur le côté de livre\) doit être 0..1 ou 1..1, afin que chaque livre a un auteur.  
  
2.  Dans **Explorateur DÉSOLÉ**, cliquez avec le bouton droit sur la classe de domaine de livre, puis cliquez sur **Ajoutez un nouveau DomainTypeDescriptor**.  
  
     Un nœud nommé **chemins d'accès des descripteurs personnalisés de propriété** s'affiche sous le nœud de **descripteur de type personnalisé** .  
  
3.  Cliquez avec le bouton droit sur le nœud de **descripteur de type personnalisé** , puis cliquez sur **Ajoutez un nouveau PropertyPath**.  
  
     Un nouveau chemin de propriété apparaît sous le nœud de **chemins d'accès des descripteurs personnalisés de propriété** .  
  
4.  Sélectionnez le nouveau chemin de propriété et, dans la fenêtre de **Propriétés** , définit **Chemin d'accès de la propriété** au chemin d'accès de l'élément de modèle approprié.  
  
     Vous pouvez modifier le chemin d'accès dans une arborescence en cliquant sur la flèche bas à droite de cette propriété.  Pour plus d'informations sur les chemins d'accès de domaine, consultez l' [Syntaxe du chemin de domaine](../modeling/domain-path-syntax.md).  Lorsque vous l'avez modifié, le chemin d'accès doit ressembler à **BookReferencesAuthor.Author\/\!Auteur**.  
  
5.  Définissez **Property** à la propriété du domaine d' **Name** de l'auteur.  
  
6.  définissez **Nom complet** au nom de l'auteur.  
  
7.  Transformez tous les modèles, générez et exécutez le langage spécifique à un domaine.  
  
8.  Dans un diagramme de modèle, créez un livre, un auteur, et liez \-les à l'aide de la relation de référence.  Sélectionnez l'élément du livre, et dans la fenêtre Propriétés vous devez voir le nom de l'auteur en plus de les propriétés du livre.  Modifiez le nom de l'auteur lié, ou liez le livre à l'auteur différent, et notez que le nom de l'auteur du livre change.  
  
## éditeurs personnalisés de propriété  
 La fenêtre propriétés fournit une expérience par défaut appropriée de modification pour le type de chaque propriété de domaine.  Par exemple, pour un type énuméré, l'utilisateur voit une liste déroulante, et pour une propriété numérique, l'utilisateur peut entrer des chiffres.  Ce principe est valable uniquement pour les types intégrés.  Si vous spécifiez un type externe, l'utilisateur sera en mesure de voir les valeurs de propriété, mais pas les modifier.  
  
 Toutefois, vous pouvez spécifier les éditeurs et les types suivants :  
  
1.  un autre éditeur qui est utilisé avec un type standard.  Par exemple, vous pouvez spécifier un éditeur de chemin d'accès à une propriété de type chaîne.  
  
2.  un type externe pour la propriété de domaine, et un éditeur pour lui.  
  
3.  Un éditeur.NET tel que l'éditeur de chemin d'accès, ou vous pouvez créer votre propre éditeur de propriétés personnalisé.  
  
     Une conversion entre un type externe et un type tel qu'une chaîne, qui a un éditeur par défaut.  
  
 Dans un langage spécifique à un domaine, *un type externe* est un type qui n'est pas l'un des types simples \(la valeur booléenne ou Int32\) ou de chaîne.  
  
#### pour définir une propriété de domaine qui a un type externe  
  
1.  dans **Explorateur de solutions**, ajoutez une référence à l'assembly \(DLL\) qui contient le type externe, dans le projet d' **Dsl** .  
  
     l'assembly peut être un assembly. NET, ou un assembly fourni par vous.  
  
2.  Ajoutez le type à la liste de **types de domaine** , à moins que vous ayez déjà fait.  
  
    1.  Ouvrez DslDefinition.dsl, et dans **Explorateur DÉSOLÉ**, cliquez avec le bouton droit sur le nœud racine, puis cliquez sur **ajoutez le nouveau type externe**.  
  
         Une nouvelle entrée apparaît sous le nœud de **types de domaine** .  
  
        > [!WARNING]
        >  L'élément de menu est sur le nœud racine DÉSOLÉ, pas le nœud de **types de domaine** .  
  
    2.  Définissez le nom et l'espace de noms du nouveau type dans la fenêtre Propriétés.  
  
3.  ajoutez une propriété de domaine à une classe de domaine de la façon habituelle.  
  
     Dans la fenêtre Propriétés, sélectionnez le type externe dans la liste déroulante dans le domaine de **Type** .  
  
 À ce stade, les utilisateurs peuvent afficher des valeurs de la propriété, mais ils ne peuvent pas la modifier.  les valeurs affichées sont obtenues à partir de la fonction d' `ToString()` .  Vous pouvez écrire un code de programme qui définit la valeur de la propriété, par exemple dans une commande ou d'une règle.  
  
### Définir un éditeur de propriétés  
 Ajoutez un attribut CLR à la propriété de domaine, sous la forme suivante :  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 vous pouvez définir l'attribut sur une propriété à l'aide de l'entrée d' **attribut personnalisé** dans la fenêtre Propriétés.  
  
 le type d' `AnEditor` doit être dérivé du type spécifié dans le deuxième paramètre.  Le deuxième paramètre doit être <xref:System.Drawing.Design.UITypeEditor> ou <xref:System.ComponentModel.ComponentEditor>.  Pour plus d'informations, consultez <xref:System.ComponentModel.EditorAttribute>.  
  
 vous pouvez spécifier votre propre éditeur, ou un éditeur fourni dans [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], tel qu' <xref:System.Windows.Forms.Design.FileNameEditor> ou <xref:System.Drawing.Design.ImageEditor>.  Par exemple, utilisez la procédure suivante pour avoir une propriété dans laquelle l'utilisateur peut entrer un nom de fichier.  
  
##### pour définir une propriété de domaine de nom de fichier  
  
1.  Ajoutez une propriété de domaine à une classe de domaine dans votre définition de langage spécifique à un domaine.  
  
2.  sélectionnez la nouvelle propriété.  Dans le champ d' **attribut personnalisé** dans la fenêtre Propriétés, entrez l'attribut suivant.  Pour écrire cet attribut, cliquez sur le bouton de sélection **\[...\]** et entrez le nom de l'attribut et les paramètres séparément :  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  laissez le type de la propriété de domaine à son paramètre par défaut de **chaîne**.  
  
4.  Pour tester l'éditeur, vérifiez que les utilisateurs peuvent ouvrir l'éditeur de nom de fichier pour éditer votre propriété de domaine.  
  
    1.  Appuyez sur CTRL\+F5 ou F5.  dans la solution de débogage, ouvrez un fichier de test.  créez un élément de la classe de domaine et sélectionnez\-le.  
  
    2.  dans la fenêtre Propriétés, sélectionnez la propriété de domaine.  Le champ de valeur indique les points de suspension **\[...\]**.  
  
    3.  Cliquez sur le bouton de sélection.  Une boîte de dialogue Fichier s'affiche.  sélectionnez un fichier et fermez la boîte de dialogue.  le chemin d'accès de fichier est maintenant la valeur de la propriété de domaine.  
  
### Définir votre propre éditeur de propriétés  
 vous pouvez définir votre propre éditeur.  Vous devez faire pour permettre à l'utilisateur l'un ou l'autre pour modifier un type que vous avez défini, ou pour modifier un type standard d'une façon particulière.  Par exemple, vous pourriez permettre à l'utilisateur d'entrer une chaîne qui représente une formule.  
  
 Vous définissez un éditeur en écrivant une classe dérivée d' <xref:System.Drawing.Design.UITypeEditor>.  votre classe doit substituer :  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, pour interagir avec l'utilisateur et mettre à jour la valeur de propriété.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, pour spécifier si votre éditeur ouvre une boîte de dialogue ou fournira un menu déroulant.  
  
 Vous pouvez également fournir une représentation graphique de la valeur de la propriété qui sera affichée dans la grille des propriétés.  Pour cela, la substitution `GetPaintValueSupported`, et l' `PaintValue`.  Pour plus d'informations, consultez <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Ajoutez le code dans un fichier distinct de code du projet d' **Dsl** .  
  
 Par exemple :  
  
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
  
 pour utiliser cet éditeur, définissez **attribut personnalisé** d'une propriété de domaine :  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Pour plus d'informations, consultez <xref:System.Drawing.Design.UITypeEditor>.  
  
## fourniture d'une liste déroulante de valeurs  
 Vous pouvez fournir une liste de valeurs pour un utilisateur a choisi de.  
  
> [!NOTE]
>  Cette technique fournit une liste de valeurs qui peuvent changer au moment de l'exécution.  si vous souhaitez fournir une liste qui ne change pas, envisagez d'utiliser à la place un type énuméré comme type de votre propriété de domaine.  
  
 Pour définir une liste de valeurs standard, vous ajoutez à votre propriété de domaine un attribut CLR qui a la forme suivante :  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Définissez une classe qui dérive de <xref:System.ComponentModel.TypeConverter>.  Ajoutez le code dans un fichier séparé dans le projet d' **Dsl** .  Par exemple :  
  
```c#  
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
  
## Voir aussi  
 [Navigation et mise à jour d'un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)