---
title: Génération de texte durant l'exécution à l'aide des modèles de texte T4
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bfbb0affe6c159f27a2568d5da35bcb98e80cdeb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939925"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Génération de texte durant l'exécution à l'aide des modèles de texte T4

Vous pouvez générer des chaînes de texte dans votre application en cours d’exécution à l’aide de modèles de texte de runtime de Visual Studio. L’ordinateur où s’exécute l’application n’a pas pour que Visual Studio. Modèles de runtime sont parfois appelés « modèles de texte prétraités », car au moment de la compilation, le modèle génère du code qui est exécuté au moment de l’exécution.

Chaque modèle est un mélange de texte tel qu’il apparaîtra dans la chaîne générée et des fragments de code de programme. Les fragments de programme fournissent des valeurs pour les parties variables de la chaîne et également de contrôler les parties conditionnelles et répétées.

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

Notez que le modèle est une page HTML dans lequel les parties variables ont été remplacés par du code de programme. Vous pouvez commencer la conception d’une telle page en écrivant un prototype statique de la page HTML. Vous pouvez ensuite remplacer la table et les autres parties variables avec du code de programme qui génère le contenu varie d’un cas à l’autre.

À l’aide d’un modèle dans votre application, il est plus facile de déterminer la forme finale de la sortie que vous pourriez le faire dans, par exemple, une longue série d’instructions d’écriture. Apporter des modifications à la forme de la sortie est plus facile et plus fiable.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Création d’un modèle de texte d’exécution dans n’importe quelle Application

### <a name="to-create-a-run-time-text-template"></a>Pour créer un modèle de texte d’exécution

1. Dans l’Explorateur de solutions, dans le menu contextuel de votre projet, choisissez **ajouter** > **un nouvel élément**.

2. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **modèle de texte Runtime**. (En Visual Basic, regardez sous **éléments communs** > **général**.)

3. Tapez un nom pour votre fichier de modèle.

    > [!NOTE]
    > Le nom du fichier modèle sera utilisé comme nom de classe dans le code généré. Par conséquent, il ne doit pas avoir d’espaces ni ponctuation.

4. Sélectionnez **Ajouter**.

    Un nouveau fichier est créé qui a l’extension **.tt**. Son **un outil personnalisé** propriété est définie sur **TextTemplatingFilePreprocessor**. Il contient les lignes suivantes :

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Conversion d’un fichier existant à un modèle au moment de l’exécution

Un bon moyen pour créer un modèle consiste à convertir un exemple existant de la sortie. Par exemple, si votre application doit générer des fichiers HTML, vous pouvez démarrer en créant un fichier HTML standard. Assurez-vous qu’elle fonctionne correctement et que son apparence est correct. Puis l’inclure dans votre projet Visual Studio et la convertir en un modèle.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Pour convertir un fichier texte existant à un modèle au moment de l’exécution

1. Insérez le fichier dans votre projet Visual Studio. Dans l’Explorateur de solutions, dans le menu contextuel du projet, choisissez **ajouter** > **élément existant**.

2. Définir le fichier **outils personnalisés** propriété **TextTemplatingFilePreprocessor**. Dans l’Explorateur de solutions, dans le menu contextuel du fichier, choisissez **propriétés**.

    > [!NOTE]
    > Si la propriété est déjà définie, assurez-vous qu’il s’agit **TextTemplatingFilePreprocessor** et non **TextTemplatingFileGenerator**. Cela peut se produire si vous incluez un fichier qui comporte déjà l’extension **.tt**.

3. Modifier l’extension de nom de fichier **.tt**. Bien que cette étape est facultative, il vous permet d’éviter l’ouverture du fichier dans un éditeur incorrect.

4. Supprimer les espaces ou la ponctuation de la partie principale du nom de fichier. Par exemple « My Web Page.tt » est incorrect, mais « MyWebPage.tt » est correct. Le nom de fichier sera utilisé comme nom de classe dans le code généré.

5. Insérez la ligne suivante au début du fichier. Si vous travaillez dans un projet Visual Basic, remplacez « C# » avec « VB ».

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Le contenu du modèle d’exécution

### <a name="template-directive"></a>Directive de modèle

Conserver la première ligne du modèle tel qu’il était lorsque vous avez créé le fichier :

`<#@ template language="C#" #>`

Le paramètre de langue dépend de la langue de votre projet.

### <a name="plain-content"></a>Contenu simple

Modifier le **.tt** fichier contient le texte que vous souhaitez générer votre application. Exemple :

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Code de programme incorporé

Vous pouvez insérer du code de programme entre `<#` et `#>`. Exemple :

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

Notez que les instructions sont insérées entre `<# ... #>` et les expressions sont insérées entre `<#= ... #>`. Pour plus d’informations, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Utilisation du modèle

### <a name="the-code-built-from-the-template"></a>Le code généré à partir du modèle

Lorsque vous enregistrez le **.tt** de fichiers, une filiale **.cs** ou **.vb** fichier est généré. Pour afficher ce fichier dans **l’Explorateur de solutions**, développez le **.tt** nœud de fichier. Dans un projet Visual Basic, choisissez d’abord **afficher tous les fichiers** dans le **l’Explorateur de solutions** barre d’outils.

Notez que le fichier auxiliaire contient une classe partielle qui contient une méthode appelée `TransformText()`. Vous pouvez appeler cette méthode à partir de votre application.

### <a name="generating-text-at-run-time"></a>Génération de texte au moment de l’exécution

Dans le code de votre application, vous pouvez générer le contenu de votre modèle à l’aide d’un appel à ceci :

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

Pour placer la classe générée dans un espace de noms particulier, définissez le **Namespace d’outil personnalisé** propriété du fichier de modèle de texte.

### <a name="debugging-runtime-text-templates"></a>Débogage des modèles de texte d’exécution

Déboguer et tester des modèles de texte d’exécution de la même façon en tant que code ordinaire.

Vous pouvez définir un point d’arrêt dans un modèle de texte. Si vous démarrez l’application en mode débogage à partir de Visual Studio, vous pouvez parcourir le code et évaluer des expressions de surveillance à l’accoutumée.

### <a name="passing-parameters-in-the-constructor"></a>Passage de paramètres dans le constructeur

Généralement un modèle doit importer des données à partir d’autres parties de l’application. Pour faciliter la tâche, le code généré par le modèle est une classe partielle. Vous pouvez créer une autre partie de la même classe dans un autre fichier dans votre projet. Ce fichier peut inclure un constructeur avec des paramètres, des propriétés et des fonctions qui sont accessibles par le code qui est incorporé dans le modèle et par le reste de l’application.

Par exemple, vous pouvez créer un fichier distinct **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

Dans votre fichier de modèle **MyWebPage.tt**, vous pouvez écrire :

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

#### <a name="constructor-parameters-in-visual-basic"></a>Paramètres du constructeur en Visual Basic

En Visual Basic, le fichier distinct **MyWebPageCode.vb** contient :

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

Le modèle peut être appelé en transmettant le paramètre dans le constructeur :

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Passage de données dans les propriétés du modèle

Une autre façon de passer des données au modèle consiste à ajouter des propriétés publiques à la classe de modèle dans une définition de classe partielle. Votre application peut définir les propriétés avant d’appeler `TransformText()`.

Vous pouvez également ajouter des champs à votre classe de modèle dans une définition partielle. Cela vous permet de passer des données entre des exécutions consécutives du modèle.

### <a name="use-partial-classes-for-code"></a>Utilisez des classes partielles pour le code

De nombreux développeurs préfèrent éviter d’écrire le corps de code volumineux dans les modèles. Au lieu de cela, vous pouvez définir des méthodes dans une classe partielle qui porte le même nom que le fichier de modèle. Appelez ces méthodes à partir du modèle. De cette façon, le modèle de montre plus clairement la chaîne de sortie cible ressemblera. Discussions sur l’apparence du résultat peuvent être séparées de la logique de création des données qu’il affiche.

### <a name="assemblies-and-references"></a>Assemblys et références

Si vous souhaitez que votre code de modèle pour référencer un .NET ou autre assembly tel que **System.Xml.dll**, ajoutez-le à votre projet **références** comme d’habitude.

Si vous souhaitez importer un espace de noms dans la même façon qu’un `using` instruction, vous pouvez le faire avec la `import` directive :

```
<#@ import namespace="System.Xml" #>
```

Ces directives doivent être placées au début du fichier, immédiatement après la `<#@template` directive.

### <a name="shared-content"></a>Contenu partagé

Si vous avez du texte qui est partagé entre plusieurs modèles, vous pouvez placer dans un fichier distinct et l’inclure dans chaque fichier dans lequel il doit apparaître :

```
<#@include file="CommonHeader.txt" #>
```

Le contenu inclus peut contenir toute combinaison de code de programme et de texte brut, et il peut contenir d’autres directives include et autres directives.

La directive include peut être utilisée n’importe où dans le texte d’un fichier de modèle ou un fichier inclus.

### <a name="inheritance-between-run-time-text-templates"></a>Héritage entre les modèles de texte de l’exécution

Vous pouvez partager du contenu entre les modèles au moment de l’exécution en écrivant un modèle de classe de base, qui peut être abstract. Utilisez le `inherits` paramètre de la `<@#template#>` directive pour référencer une autre classe de modèle de runtime.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Modèle d’héritage : Fragments dans les méthodes de Base

Dans le modèle utilisé dans l’exemple suivant, notez les points suivants :

- La classe de base `SharedFragments` définit des méthodes dans les blocs de fonctionnalité de classe `<#+ ... #>`.

- La classe de base ne contient aucun texte libre. Au lieu de cela, tous ses blocs de texte se produisent à l’intérieur des méthodes de la fonctionnalité de classe.

- La classe dérivée appelle les méthodes définies dans `SharedFragments`.

- L’application appelle le `TextTransform()` méthode de la classe dérivée, mais ne transforme ne pas la classe de base `SharedFragments`.

- Les classes de base et dérivées sont des modèles de texte du runtime ; Autrement dit, le **un outil personnalisé** propriété est définie sur **TextTemplatingFilePreprocessor**.

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

**MyProgram.cs :**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Le résultat obtenu :**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Modèle d’héritage : Texte dans le corps de Base

Dans cette approche alternative à l’aide de l’héritage de modèle, la majeure partie du texte est définie dans le modèle de base. Les modèles dérivés fournissent des données et les fragments de texte qui s’intègrent pas le contenu de base.

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

**Code d’application :**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Sortie obtenue :**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Rubriques connexes

Modèles de conception : Si vous souhaitez utiliser un modèle pour générer du code qui devient partie intégrante de votre application, consultez [génération de Code au moment du Design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Modèles de l’exécution peuvent être utilisés dans n’importe quelle application où les modèles et leur contenu sont déterminés au moment de la compilation. Toutefois, si vous souhaitez écrire une extension Visual Studio qui génère du texte à partir de modèles qui changent au moment de l’exécution, consultez [appel d’une Transformation de texte dans une Extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Voir aussi

- [Génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)
- [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)
- [Boîte à outils T4](http://olegsych.com/T4Toolbox/)
