---
title: "Procédure pas à pas : génération de code à l'aide de modèles de texte"
description: Découvrez que la génération de code vous permet de générer du code de programme qui est fortement typé et qui peut être facilement modifié quand le modèle source change.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22940fb86ab0cfd7262a3ca7845521847add2dff
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388124"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Procédure pas à pas : générer du code à l’aide de modèles de texte

La génération de code vous permet de générer du code de programme qui est fortement typé mais peut être facilement modifié quand le modèle source change. Comparez ceci avec l’autre technique consistant à écrire un programme complètement générique qui accepte un fichier de configuration, qui est plus flexible mais génère du code qui n’est pas aussi facile à lire et à modifier et n’offre pas d’aussi bonnes performances. Cette procédure pas à pas montre les avantages offerts par la génération de code.

## <a name="typed-code-for-reading-xml"></a>Code typé pour lire des données XML

L’espace de noms System.Xml fournit des outils complets pour charger un document XML puis y accéder librement en mémoire. Malheureusement, tous les nœuds ont le même type, XmlNode. Ainsi, il est très facile de commettre des erreurs de programmation, par exemple attendre le type de nœud enfant incorrect ou les attributs incorrects.

Dans cet exemple de projet, un modèle lit un exemple de fichier XML et génère des classes qui correspondent à chaque type de nœud. Dans le code écrit manuellement, vous pouvez utiliser ces classes pour parcourir le fichier XML. Vous pouvez également exécuter votre application sur tout autre fichier qui utilise les mêmes types de nœuds. L’objectif de l’exemple de fichier XML est de fournir des exemples de tous les types de nœuds que vous souhaitez que votre application puisse gérer.

> [!NOTE]
> L' [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe)d’application, qui est inclus dans Visual Studio, peut générer des classes fortement typées à partir de fichiers XML. Le modèle présenté ici est fourni comme exemple.

Voici l’exemple de fichier :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

Dans le projet construit par cette procédure pas à pas, vous pouvez écrire du code semblable au suivant et IntelliSense vous présente les noms corrects des enfants et des attributs à mesure que vous tapez :

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

Comparez cela avec le code non typé que vous pouvez écrire sans le modèle :

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

Dans la version fortement typée, une modification apportée au schéma XML entraîne des modifications des classes. Le compilateur met en surbrillance les parties du code d’application qui doivent être modifiées. Dans la version non typée qui utilise du code XML générique, cette prise en charge n’existe pas.

Dans ce projet, un seul fichier de modèle est utilisé pour générer les classes qui rendent la version typée possible.

## <a name="set-up-the-project"></a>Configurer le projet

### <a name="create-or-open-a-c-project"></a>Créer ou ouvrir un projet C#

Vous pouvez appliquer cette technique à tout projet de code. Cette procédure pas à pas utilise un projet C#, et à des fins de test nous utilisons une application console.

1. Dans le menu **fichier** , cliquez sur **nouveau** , puis sur **projet**.

2. Cliquez sur le nœud **Visual C#** puis, dans le volet **Modèles** , cliquez sur **Application console**.

### <a name="add-a-prototype-xml-file-to-the-project"></a>Ajouter un fichier XML de prototype au projet

L’objectif de ce fichier consiste à fournir des exemples des types de nœuds XML que vous souhaitez que votre application puisse lire. Il peut s’agir d’un fichier qui sera utilisé pour tester votre application. Le modèle produira une classe C# pour chaque type de nœud dans ce fichier.

Le fichier doit faire partie du projet pour que le modèle puisse le lire, mais il ne sera pas généré dans l’application compilée.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter** , puis sur **nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier XML** dans le volet **Modèles** .

3. Ajoutez votre exemple de contenu au fichier.

4. Pour cette procédure pas à pas, nommez le fichier `exampleXml.xml`. Définissez le code XML fourni dans la section précédente comme contenu du fichier.

### <a name="add-a-test-code-file"></a>Ajouter un fichier de code de test

Ajoutez un fichier C# à votre projet et placez-y un exemple du code que vous souhaitez pouvoir écrire. Exemple :

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

À ce stade, la compilation de ce code échouera. À mesure que vous écrivez le modèle, vous allez générer des classes qui permettent à la compilation de réussir.

Un test plus complet pourrait vérifier le résultat de cette fonction de test par rapport au contenu connu de l’exemple de fichier XML. Toutefois, dans cette procédure pas à pas nous nous satisferons de la réussite de la compilation de la méthode de test.

### <a name="add-a-text-template-file"></a>Ajouter un fichier de modèle de texte

Ajoutez un fichier de modèle de texte et définissez l’extension de sortie sur *. cs*.

1. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Modèle de texte** dans le volet **Modèles** .

    > [!NOTE]
    > Vérifiez que vous ajoutez bien un Modèle de texte, et non un Modèle de texte prétraité.

3. Dans le fichier, dans la directive de modèle, affectez la valeur `hostspecific` à l’attribut `true`.

     Cette modification permettra au code de modèle d’accéder aux services Visual Studio.

4. Dans la directive de sortie, affectez « .cs » comme attribut d’extension, pour que le modèle génère un fichier C#. Dans un projet Visual Basic, vous choisiriez « .vb ».

5. Enregistrez le fichier . À ce stade, le fichier de modèle de texte doit contenir ces lignes :

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Notez qu’un fichier .cs apparaît dans l’Explorateur de solutions comme fichier auxiliaire du fichier de modèle. Vous pouvez le voir en cliquant sur [+] en regard du nom du fichier de modèle. Ce fichier est généré à partir du fichier de modèle chaque fois que vous enregistrez ou déplacez le focus hors du fichier de modèle. Le fichier généré sera compilé dans le cadre de votre projet.

Pour plus de commodité pendant que vous développez le fichier de modèle, réorganisez les fenêtres du fichier de modèle et du fichier généré pour les visualiser les unes à côté des autres. Cela vous permet de voir immédiatement le résultat de votre modèle. Vous remarquerez également que quand votre modèle génère du code C# non valide, des erreurs sont affichées dans la fenêtre de message d’erreur.

Toute modification que vous effectuez directement dans le fichier généré sera perdue chaque fois que vous enregistrerez le fichier de modèle. Vous devez donc éviter de modifier le fichier généré, ou le modifier uniquement pour de courts tests. Il est parfois utile de tester un petit fragment de code dans le fichier généré, où IntelliSense fonctionne, puis de le copier dans le fichier de modèle.

## <a name="develop-the-text-template"></a>Développer le modèle de texte

En suivant les recommandations en matière de développement agile, nous allons développer le modèle par petites étapes, en supprimant certaines erreurs à chaque incrément, jusqu’à ce que le code de test se compile et s’exécute correctement.

### <a name="prototype-the-code-to-be-generated"></a>Prototyper le code à générer

Le code de test nécessite une classe pour chaque nœud dans le fichier. Ainsi, certaines des erreurs de compilation disparaîtront si vous ajoutez les lignes suivantes au modèle et que vous l’enregistrez ensuite :

```csharp
class Catalog {}
class Artist {}
class Song {}
```

Cela vous aide à voir ce qui est nécessaire, mais les déclarations doivent être générées à partir des types de nœuds dans l’exemple de fichier XML. Supprimez ces lignes expérimentales du modèle.

### <a name="generate-application-code-from-the-model-xml-file"></a>Générer du code d’application à partir du fichier XML de modèle

Pour lire le fichier XML et générer des déclarations de classe, remplacez le contenu du modèle par le code de modèle suivant :

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

Remplacez le chemin de fichier par le chemin correct pour votre projet.

Notez les délimiteurs de bloc de code `<#...#>`. Ces délimiteurs encadrent un fragment du code du programme qui génère le texte. Les délimiteurs de bloc d’expression `<#=...#>` encadrent une expression qui peut être évaluée comme chaîne.

Quand vous écrivez un modèle qui génère du code source pour votre application, vous êtes confronté à deux textes de programme distincts. Le programme contenu dans les délimiteurs de bloc de code s’exécute chaque fois que vous enregistrez le modèle ou que vous déplacez le focus vers une autre fenêtre. Le texte qu’il génère, qui apparaît hors des délimiteurs, est copié dans le fichier généré et devient partie intégrante de votre code d’application.

La directive `<#@assembly#>` se comporte comme une référence, mettant l’assembly à disposition du code de modèle. La liste des assemblys visibles par le modèle est distincte de la liste de références dans le projet d’application.

La directive `<#@import#>` agit comme une instruction `using` et vous permet d’utiliser les noms courts des classes dans l’espace de noms importé.

Malheureusement, bien que ce modèle génère du code, il produit une déclaration de classe pour chaque nœud dans l’exemple de fichier XML. Ainsi, s’il existe plusieurs instances du nœud `<song>` , plusieurs déclarations de la classe song apparaissent.

### <a name="read-the-model-file-then-generate-the-code"></a>Lire le fichier de modèle, puis générer le code

De nombreux modèles de texte suivent un modèle dans lequel la première partie du modèle lit le fichier source et la deuxième génère le modèle. Nous devons lire l’intégralité de l’exemple de fichier pour récapituler les types de nœuds qu’il contient, puis générer les déclarations de classe. Un autre `<#@import#>` est nécessaire pour que nous puissions utiliser `Dictionary<>:`.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Ajouter une méthode auxiliaire

Un bloc de contrôle de fonctionnalité de classe est un bloc dans lequel vous pouvez définir des méthodes auxiliaires. Le bloc est délimité par `<#+...#>` et il doit apparaître comme dernier bloc dans le fichier.

Si vous préférez que les noms de classes commencent par une lettre majuscule, vous pouvez remplacer la dernière partie du modèle par le code de modèle suivant :

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

À ce niveau, le fichier *. cs* généré contient les déclarations suivantes :

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Vous pouvez ajouter plus de détails tels que les propriétés des nœuds enfants, des attributs et du texte interne à l’aide de la même approche.

### <a name="access-the-visual-studio-api"></a>Accéder à l’API Visual Studio

La définition `hostspecific` de l’attribut de la `<#@template#>` directive permet au modèle d’obtenir l’accès à l’API Visual Studio. Le modèle peut utiliser cette API pour obtenir l’emplacement des fichiers projet, pour éviter d’utiliser un chemin absolu dans le code du modèle.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>Compléter le modèle de texte

Le contenu de modèle suivant génère du code qui permet de compiler et d’exécuter le code de test.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>Exécuter le programme de test

Dans la partie principale de l’application console, les lignes suivantes exécutent la méthode de test. Appuyez sur F5 pour exécuter le programme en mode débogage :

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>Écrire et mettre à jour l’application

L’application peut désormais être écrite dans un style fortement typé, en utilisant les classes générées plutôt que du code XML générique.

Quand le schéma XML change, de nouvelles classes peuvent facilement être générées. Le compilateur indiquera au développeur l’endroit où le code d’application doit être mis à jour.

Pour régénérer les classes lorsque l’exemple de fichier XML est modifié, cliquez sur **transformer tous les modèles** dans la barre d’outils **Explorateur de solutions** .

## <a name="conclusion"></a>Conclusion

Cette procédure pas à pas illustre plusieurs techniques et avantages de la génération de code :

- La *génération de code* est la création d’une partie du code source de votre application à partir d’un *modèle*. Le modèle contient des informations dans un format adapté au domaine d’application, et il peut changer pendant la durée de vie de l’application.

- Le typage fort est l’un des avantages de la génération de code. Tandis que le modèle représente les informations dans un format plus adapté à l’utilisateur, le code généré permet à d’autres parties de l’application de traiter les informations à l’aide d’un ensemble de types.

- IntelliSense et le compilateur vous aident à créer du code conforme au schéma du modèle, à la fois quand vous écrivez du nouveau code et quand le schéma est mis à jour.

- Ces avantages peuvent être obtenus grâce à l’ajout d’un fichier de modèle simple et unique à un projet.

- Un modèle de texte peut être développé et testé rapidement et de façon incrémentielle.

Dans cette procédure pas à pas, le code du programme est généré à partir d’une instance du modèle, un exemple représentatif des fichiers XML que l’application traitera. Dans une approche plus formelle, le schéma XML serait l’entrée du modèle, sous la forme d’un fichier .xsd ou d’une définition de langage propre au domaine. Cette approche faciliterait pour le modèle la détermination de caractéristiques telles que la multiplicité d’une relation.

## <a name="troubleshoot-the-text-template"></a>Résoudre les problèmes liés au modèle de texte

Si vous avez vu des erreurs de compilation ou de transformation du modèle dans la **Liste d’erreurs** ou si le fichier de sortie n’a pas été généré correctement, vous pouvez résoudre les problèmes du modèle de texte avec les techniques décrites dans [Génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

## <a name="see-also"></a>Voir aussi

- [Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Écriture d'un modèle de texte T4](../modeling/writing-a-t4-text-template.md)
