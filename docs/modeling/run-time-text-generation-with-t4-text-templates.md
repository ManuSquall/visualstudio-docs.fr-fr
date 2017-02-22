---
title: "Run-Time Text Generation with T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Preprocessed Text Template project item"
  - "TextTemplatingFilePreprocessor custom tool"
  - "text templates, TransformText() method"
  - "text templates, generating files at run time"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 22
---
# Run-Time Text Generation with T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez générer des chaînes de texte dans votre application en cours d'exécution à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèles de texte runtime.  Il n'est pas nécessaire que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soit installé sur l'ordinateur sur lequel l'application s'exécute.  Modèles Runtime sont parfois appelés « prétraité des modèles de texte » parce qu'au moment de la compilation, le modèle génère du code qui est exécuté au moment de l'exécution.  
  
 Chaque modèle combine le texte tel qu'il apparaîtra dans la chaîne générée et des fragments de code de programme.  Les fragments de programme fournissent des valeurs pour les parties variables de la chaîne et contrôlent par ailleurs les parties conditionnelles et répétées.  
  
 Par exemple, le modèle suivant peut être utilisé dans une application qui crée un rapport HTML.  
  
```  
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
  
 Remarquez que le modèle est une page HTML dans laquelle les parties variables ont été remplacées par du code de programme.  Vous pouvez commencer la conception de cette page en écrivant un prototype statique de la page HTML.  Vous pouvez ensuite remplacer la table et les autres parties variables par du code de programme générant le contenu qui varie d'un cas à l'autre.  
  
 Grâce à l'utilisation d'un modèle dans votre application, il est plus facile de visualiser la forme finale de la sortie que, par exemple, dans une longue série d'instructions d'écriture.  La modification de la forme de la sortie est plus facile et plus fiable.  
  
## Création d'un modèle de texte au moment de l'exécution dans n'importe quelle application  
  
#### Pour créer un modèle de texte au moment de l'exécution  
  
1.  Dans l'Explorateur de solutions, dans le menu contextuel de votre projet, choisissez  **Add**,  **Un nouvel élément**.  
  
2.  Dans la  **Ajouter un nouvel élément** boîte de dialogue, sélectionnez  **Modèle de texte Runtime**.  \(Dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] regardez sous **Éléments communs\\Général**.\)  
  
3.  Tapez un nom pour votre fichier modèle.  
  
    > [!NOTE]
    >  Le nom du fichier modèle sera utilisé comme nom de classe dans le code généré.  Par conséquent, il ne doit pas comporter d'espace ni de signe de ponctuation.  
  
4.  Choisissez  **Ajouter**.  
  
     Un nouveau fichier comportant l'extension **.tt** est créé.  Sa propriété **Outil personnalisé** a la valeur **TextTemplatingFilePreprocessor**.  Il contient les lignes suivantes :  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## Conversion d'un fichier existant en modèle au moment de l'exécution  
 La conversion d'un exemple existant de la sortie est un moyen efficace de créer un modèle.  Par exemple, si votre application doit générer des fichiers HTML, vous pouvez commencer par créer un fichier HTML simple.  Vérifiez qu'il fonctionne de façon appropriée et que son apparence est correcte.  Incluez\-le ensuite dans votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et convertissez\-le en modèle.  
  
#### Pour convertir un fichier texte existant en modèle au moment de l'exécution  
  
1.  Incluez le fichier dans votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Dans l'Explorateur de solutions, dans le menu contextuel du projet, choisissez  **Add**,  **Un élément existant**.  
  
2.  Affectez à la propriété **Outil personnalisé** du fichier la valeur **TextTemplatingFilePreprocessor**.  Dans l'Explorateur de solutions, dans le menu contextuel du fichier, choisissez  **Propriétés**.  
  
    > [!NOTE]
    >  Si la propriété a déjà une valeur, assurez\-vous qu'il s'agit de **TextTemplatingFilePreprocessor**, et non pas de **TextTemplatingFileGenerator**.  Cela peut se produire si vous incluez un fichier qui comporte déjà l'extension **.tt**.  
  
3.  Attribuez l'extension de nom de fichier **.tt** au fichier.  Bien que cette étape soit facultative, elle vous empêche d'ouvrir le fichier dans un éditeur incorrect.  
  
4.  Supprimez tous les espaces ou signes de ponctuation de la partie principale du nom de fichier.  Par exemple, « My Web Page.tt » est incorrect, mais « MyWebPage.tt » est correct.  Le nom de fichier sera utilisé comme nom de classe dans le code généré.  
  
5.  Insérez la ligne suivante au début du fichier.  Si vous travaillez dans un projet Visual Basic, remplacez "C\#" par "VB".  
  
     `<#@ template language="C#" #>`  
  
## Contenu du modèle au moment de l'exécution  
  
### Directive du modèle  
 Conservez la première ligne du modèle telle qu'elle était lorsque vous avez créé le fichier :  
  
 `<#@ template language="C#" #>`  
  
 Le paramètre de langage dépendra du langage de votre projet.  
  
### Contenu simple  
 Modifiez le fichier **.tt** de façon à ce qu'il contienne le texte que votre application doit générer.  Par exemple :  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### Code de programme incorporé  
 Vous pouvez insérer du code de programme entre `<#` et `#>`.  Par exemple :  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
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
  
 Notez que les instructions sont insérées entre `<# ... #>` et que les expressions sont insérées entre `<#= ... #>`.  Pour plus d'informations, consultez [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Utilisation du modèle  
  
### Code généré à partir du modèle  
 Chaque fois que vous enregistrez le fichier **.tt**, un fichier **.cs** ou **.vb** subsidiaire est généré.  Pour afficher ce fichier dans l'Explorateur de solutions, développez le nœud de fichier **.tt**.  Dans un projet Visual Basic, vous pourrez développer le nœud après avoir cliqué sur **Afficher tous les fichiers** dans la barre d'outils de l'Explorateur de solutions.  
  
 Notez que ce fichier subsidiaire contient une classe partielle qui inclut une méthode appelée `TransformText()`.  Vous pouvez appeler cette méthode à partir de votre application.  
  
### Génération de texte au moment de l'exécution  
 Dans votre code d'application, vous pouvez générer le contenu de votre modèle à l'aide d'un appel tel que celui\-ci :  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 Pour placer la classe générée dans un espace de noms particulier, définissez la propriété **Espace de noms de l'outil personnalisé** du fichier de modèle de texte.  
  
### Débogage des modèles de texte d'exécution  
 Déboguer et tester des modèles de texte runtime de la même manière que le code ordinaire.  
  
 Vous pouvez définir un point d'arrêt dans un modèle de texte.  Si vous démarrez l'application en mode débogage à partir de Visual Studio, vous pouvez parcourir le code et évaluer des expressions espionnes dans la manière habituelle.  
  
### Passage de paramètres dans le constructeur  
 Un modèle doit généralement importer des données d'autres parties de l'application.  Pour simplifier cette opération, le code généré par le modèle est une classe partielle.  Vous pouvez créer une autre partie de la même classe dans un autre fichier de votre projet.  Ce fichier peut inclure un constructeur avec des paramètres, des propriétés et des fonctions accessibles à la fois par le code incorporé dans le modèle et par le reste de l'application.  
  
 Par exemple, vous pouvez créer un fichier séparé **MyWebPageCode.cs** :  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 Dans votre fichier modèle **MyWebPage.tt**, vous pouvez écrire :  
  
```c#  
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
  
 Pour utiliser ce modèle dans l'application :  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Paramètres de constructeur en Visual Basic  
 Dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], le fichier séparé **MyWebPageCode.vb** contient ce qui suit :  
  
```vb#  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 Le fichier modèle peut contenir ce qui suit :  
  
```vb#  
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
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### Passage de données dans des propriétés de modèle  
 Une autre méthode de passage des données au modèle consiste à ajouter des propriétés publiques à la classe de modèle dans une définition de classe partielle.  Votre application peut définir les propriétés avant d'appeler `TransformText()`.  
  
 Vous pouvez également ajouter des champs à votre classe de modèle dans une définition partielle.  Cela vous permet de passer des données entre des exécutions consécutives du modèle.  
  
### Utilisation de classes partielles pour le code  
 De nombreux développeurs préfèrent éviter l'écriture de corps de code volumineux dans les modèles.  À la place, définissez des méthodes dans une classe partielle portant le même nom que le fichier modèle.  Appelez ces méthodes à partir du modèle.  De cette façon, le modèle vous montre plus clairement à quoi ressemblera la chaîne de sortie cible.  Les discussions relatives à l'apparence du résultat peuvent être séparées de la logique de création des données qu'il affiche.  
  
### Assemblys et références  
 Si vous voulez que le code de votre modèle référence un assembly .NET ou un autre assembly tel que **System.Xml.dll**, vous devez l'ajouter aux **références** de votre projet de la façon habituelle.  
  
 Si vous voulez importer un espace de noms de la même façon qu'une instruction `using`, vous en avez la possibilité avec la directive `import` :  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Ces directives doivent être placées au début du fichier, immédiatement après la directive `<#@template`.  
  
### Contenu partagé  
 Si plusieurs modèles partagent du texte, vous pouvez le placer dans un fichier séparé et l'inclure dans chaque fichier où il doit apparaître :  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 Le contenu inclus peut comporter toute combinaison de code de programme et de texte brut, ainsi que d'autres directives include et d'autres directives.  
  
 La directive include peut être utilisée n'importe où dans le texte d'un fichier modèle ou d'un fichier inclus.  
  
### Héritage entre les modèles de texte au moment de l'exécution  
 Vous pouvez partager le contenu entre des modèles au moment de l'exécution en écrivant un modèle de classe de base, qui peut être abstrait.  Utilisation du `inherits` paramètre de la `<@#template#>` directive pour faire référence à une autre classe de modèle d'exécution.  
  
#### Modèle d'héritage : fragments dans les méthodes de base  
 Dans le modèle utilisé dans l'exemple qui suit, remarquez les points suivants :  
  
-   La classe de base `SharedFragments` définit des méthodes dans les blocs de fonctionnalité de classe `<#+ ... #>`.  
  
-   La classe de base ne contient pas de texte libre.  À la place, tous ses blocs de texte se produisent à l'intérieur des méthodes de fonctionnalité de classe.  
  
-   La classe dérivée appelle les méthodes définies dans `SharedFragments`.  
  
-   L'application appelle la méthode `TextTransform()` de la classe dérivée, mais ne transforme pas la classe de base `SharedFragments`.  
  
-   Les classes de base et dérivées sont des modèles de texte runtime : autrement dit, la  **Custom Tool** propriété est définie sur  **TextTemplatingFilePreprocessor**.  
  
 **SharedFragments.tt :**  
  
```c#  
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
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs :**  
  
```c#  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Résultat :**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### Modèle d'héritage : texte dans le corps de base  
 Dans cette approche alternative de l'utilisation de l'héritage de modèle, l'ensemble du texte est défini dans le modèle de base.  Les modèles dérivés fournissent des données et des fragments de texte qui s'intègrent au contenu de base.  
  
 **AbstractBaseTemplate1.tt :**  
  
```c#  
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
  
```c#  
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
  
 **Code d'application :**  
  
```c#  
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
  
## Rubriques connexes  
 Modèles au moment du design : si vous voulez utiliser un modèle pour générer du code qui devient partie intégrante de votre application, consultez [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Modèles de runtime peuvent être utilisés dans n'importe quelle application où les modèles et leur contenu sont déterminés au moment de la compilation.  En revanche, si vous voulez écrire une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] générant du texte à partir de modèles qui changent au moment de l'exécution, consultez [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Voir aussi  
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)   
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)   
 [Compréhension T4 : Prétraité des modèles de texte par Oleg sous](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)