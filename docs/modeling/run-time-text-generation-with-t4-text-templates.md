---
title: Génération de texte durant l'exécution à l'aide des modèles de texte T4
description: Découvrez comment vous pouvez générer des chaînes de texte dans votre application au moment de l’exécution à l’aide des modèles de texte du runtime Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387552"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Génération de texte durant l'exécution à l'aide des modèles de texte T4

Vous pouvez générer des chaînes de texte dans votre application au moment de l’exécution à l’aide des modèles de texte du runtime Visual Studio. L’ordinateur sur lequel l’application s’exécute n’a pas besoin de disposer de Visual Studio. Les modèles Runtime sont parfois appelés « modèles de texte prétraités », car au moment de la compilation, le modèle génère du code qui est exécuté au moment de l’exécution.

Chaque modèle est une combinaison du texte tel qu’il apparaîtra dans la chaîne générée et des fragments de code de programme. Les fragments de programme fournissent des valeurs pour les parties variables de la chaîne, et contrôlent également les parties conditionnelles et répétées.

Par exemple, le modèle suivant peut être utilisé dans une application qui crée un rapport HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Notez que le modèle est une page HTML dans laquelle les parties variables ont été remplacées par du code de programme. Vous pouvez commencer la conception d’une telle page en écrivant un prototype statique de la page HTML. Vous pouvez ensuite remplacer la table et d’autres parties variables par du code de programme qui génère le contenu qui varie d’une fois à l’autre.

À l’aide d’un modèle dans votre application, il est plus facile de voir la forme finale de la sortie que vous ne le pouviez dans, par exemple, une longue série d’instructions Write. Apporter des modifications au formulaire de sortie est plus simple et plus fiable.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Création d’un modèle de texte Run-Time dans une application

### <a name="to-create-a-run-time-text-template"></a>Pour créer un modèle de texte au moment de l’exécution

1. Dans Explorateur de solutions, dans le menu contextuel de votre projet, choisissez **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **modèle de texte Runtime**. (Dans Visual Basic regarder sous **éléments communs**  >  **Général**.)

3. Tapez un nom pour votre fichier de modèle.

    > [!NOTE]
    > Le nom du fichier de modèle sera utilisé comme nom de classe dans le code généré. Par conséquent, il ne doit pas contenir d’espaces ni de signes de ponctuation.

4. Choisissez **Ajouter**.

    Un nouveau fichier avec l’extension **. TT** est créé. Sa propriété **outil personnalisé** est définie sur **valeur TextTemplatingFilePreprocessor**. Il contient les lignes suivantes :

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Conversion d’un fichier existant en modèle Run-Time

Un bon moyen de créer un modèle consiste à convertir un exemple existant de la sortie. Par exemple, si votre application génère des fichiers HTML, vous pouvez commencer par créer un fichier HTML brut. Assurez-vous qu’il fonctionne correctement et que son apparence est correcte. Ensuite, incluez-le dans votre projet Visual Studio et convertissez-le en modèle.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Pour convertir un fichier texte existant en modèle au moment de l’exécution

1. Incluez le fichier dans votre projet Visual Studio. Dans Explorateur de solutions, dans le menu contextuel du projet, choisissez **Ajouter** un  >  **élément existant**.

2. Définissez la propriété **outils personnalisés** du fichier sur **valeur TextTemplatingFilePreprocessor**. Dans Explorateur de solutions, dans le menu contextuel du fichier, choisissez **Propriétés**.

    > [!NOTE]
    > Si la propriété est déjà définie, assurez-vous qu’il s’agit de **valeur TextTemplatingFilePreprocessor** et non de **TextTemplatingFileGenerator**. Cela peut se produire si vous incluez un fichier qui a déjà l’extension **. TT**.

3. Remplacez l’extension de nom de fichier par **. TT**. Bien que cette étape soit facultative, elle vous permet d’éviter d’ouvrir le fichier dans un éditeur incorrect.

4. Supprimez les espaces ou la ponctuation de la partie principale du nom de fichier. Par exemple, « mon Page.tt Web » serait incorrect, mais « MyWebPage.tt » est correct. Le nom de fichier sera utilisé comme nom de classe dans le code généré.

5. Insérez la ligne suivante au début du fichier. Si vous travaillez dans un projet Visual Basic, remplacez « C# » par « VB ».

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Contenu du modèle Run-Time

### <a name="template-directive"></a>Directive de modèle

Conservez la première ligne du modèle telle qu’elle était lors de la création du fichier :

`<#@ template language="C#" #>`

Le paramètre Language dépend de la langue de votre projet.

### <a name="plain-content"></a>Contenu brut

Modifiez le fichier **. TT** pour qu’il contienne le texte que vous souhaitez que votre application génère. Exemple :

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Code du programme incorporé

Vous pouvez insérer du code de programme entre `<#` et `#>` . Exemple :

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Notez que les instructions sont insérées entre `<# ... #>` et les expressions sont insérées entre `<#= ... #>` . Pour plus d’informations, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Utilisation du modèle

### <a name="the-code-built-from-the-template"></a>Code généré à partir du modèle

Lorsque vous enregistrez le fichier **. TT** , un fichier. **CS** ou **. vb** subsidiaire est généré. Pour afficher ce fichier dans **Explorateur de solutions**, développez le nœud de fichier **. TT** . Dans un projet Visual Basic, choisissez tout d’abord **Afficher tous les fichiers** dans la barre d’outils **Explorateur de solutions** .

Notez que le fichier subsidiaire contient une classe partielle qui contient une méthode appelée `TransformText()` . Vous pouvez appeler cette méthode à partir de votre application.

### <a name="generating-text-at-run-time"></a>Génération de texte au moment de l’exécution

Dans votre code d’application, vous pouvez générer le contenu de votre modèle à l’aide d’un appel de la façon suivante :

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Pour placer la classe générée dans un espace de noms particulier, définissez la propriété espace de noms de l' **outil personnalisé** du fichier de modèle de texte.

### <a name="debugging-runtime-text-templates"></a>Débogage des modèles de texte du Runtime

Déboguez et testez les modèles de texte à l’exécution de la même façon que le code ordinaire.

Vous pouvez définir un point d’arrêt dans un modèle de texte. Si vous démarrez l’application en mode débogage à partir de Visual Studio, vous pouvez effectuer un pas à pas détaillé dans le code et évaluer les expressions Watch de la façon habituelle.

### <a name="passing-parameters-in-the-constructor"></a>Passage de paramètres dans le constructeur

En général, un modèle doit importer des données à partir d’autres parties de l’application. Pour faciliter cette opération, le code généré par le modèle est une classe partielle. Vous pouvez créer une autre partie de la même classe dans un autre fichier de votre projet. Ce fichier peut inclure un constructeur avec des paramètres, des propriétés et des fonctions accessibles à la fois par le code incorporé dans le modèle et par le reste de l’application.

Par exemple, vous pouvez créer un fichier distinct **MyWebPageCode. cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

Dans votre fichier de modèle **MyWebPage.TT**, vous pouvez écrire :

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Pour utiliser ce modèle dans l’application :

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Paramètres de constructeur dans Visual Basic

Dans Visual Basic, le fichier distinct **MyWebPageCode. vb** contient les éléments suivants :

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Le fichier de modèle peut contenir :

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Le modèle peut être appelé en passant le paramètre dans le constructeur :

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Passage de données dans les propriétés de modèle

Une autre façon de passer des données au modèle consiste à ajouter des propriétés publiques à la classe de modèle dans une définition de classe partielle. Votre application peut définir les propriétés avant d’appeler `TransformText()` .

Vous pouvez également ajouter des champs à votre classe de modèle dans une définition partielle. Cela vous permet de passer des données entre les exécutions consécutives du modèle.

### <a name="use-partial-classes-for-code"></a>Utiliser des classes partielles pour le code

De nombreux développeurs préfèrent éviter d’écrire de grands corps de code dans des modèles. Au lieu de cela, vous pouvez définir des méthodes dans une classe partielle qui porte le même nom que le fichier de modèle. Appelez ces méthodes à partir du modèle. De cette façon, le modèle affiche plus clairement à quoi ressemble la chaîne de sortie cible. Les discussions sur l’apparence du résultat peuvent être séparées de la logique de création des données qu’il affiche.

### <a name="assemblies-and-references"></a>Assemblys et références

Si vous souhaitez que votre code de modèle référence un assembly .NET ou un autre assembly tel que **System.Xml.dll**, ajoutez-le aux **références** de votre projet de la manière habituelle.

Si vous souhaitez importer un espace de noms de la même façon qu’une `using` instruction, vous pouvez le faire avec la `import` directive :

```
<#@ import namespace="System.Xml" #>
```

Ces directives doivent être placées au début du fichier, immédiatement après la `<#@template` directive.

### <a name="shared-content"></a>Contenu partagé

Si vous disposez d’un texte partagé entre plusieurs modèles, vous pouvez le placer dans un fichier distinct et l’inclure dans chaque fichier dans lequel il doit apparaître :

```
<#@include file="CommonHeader.txt" #>
```

Le contenu inclus peut contenir n’importe quelle combinaison de code de programme et de texte brut, et il peut contenir d’autres directives include et d’autres directives.

La directive include peut être utilisée n’importe où dans le texte d’un fichier de modèle ou dans un fichier inclus.

### <a name="inheritance-between-run-time-text-templates"></a>Héritage entre les modèles de texte Run-Time

Vous pouvez partager du contenu entre les modèles au moment de l’exécution en écrivant un modèle de classe de base, qui peut être abstrait. Utilisez le `inherits` paramètre de la `<@#template#>` directive pour référencer une autre classe de modèle d’exécution.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Modèle d’héritage : fragments dans les méthodes de base

Dans le modèle utilisé dans l’exemple qui suit, notez les points suivants :

- La classe de base `SharedFragments` définit des méthodes dans des blocs de fonctionnalité de classe `<#+ ... #>` .

- La classe de base ne contient pas de texte libre. Au lieu de cela, tous ses blocs de texte se produisent à l’intérieur des méthodes de fonctionnalité de classe.

- La classe dérivée appelle les méthodes définies dans `SharedFragments` .

- L’application appelle la `TextTransform()` méthode de la classe dérivée, mais ne transforme pas la classe de base `SharedFragments` .

- Les classes de base et les classes dérivées sont des modèles de texte d’exécution ; autrement dit, la propriété de l' **outil personnalisé** est définie sur **valeur TextTemplatingFilePreprocessor**.

**SharedFragments.tt :**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt :**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram. cs :**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Résultat obtenu :**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Modèle d’héritage : texte dans le corps de base

Dans cette approche alternative à l’utilisation de l’héritage de modèle, la majeure partie du texte est définie dans le modèle de base. Les modèles dérivés fournissent des données et des fragments de texte qui tiennent dans le contenu de base.

**AbstractBaseTemplate1.tt :**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt :**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Code de l’application :**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Résultat :**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Rubriques connexes

Modèles au moment du design : Si vous souhaitez utiliser un modèle pour générer du code qui devient partie intégrante de votre application, consultez [génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Les modèles au moment de l’exécution peuvent être utilisés dans n’importe quelle application où les modèles et leur contenu sont déterminés au moment de la compilation. Toutefois, si vous souhaitez écrire une extension Visual Studio qui génère du texte à partir de modèles qui changent au moment de l’exécution, consultez appel de la [transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Voir aussi

- [Génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)
- [Écriture d'un modèle de texte T4](../modeling/writing-a-t4-text-template.md)
- [Boîte à outils T4](http://olegsych.com/T4Toolbox/)
