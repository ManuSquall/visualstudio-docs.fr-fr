---
title: Génération de code durant la conception à l'aide de modèles de texte T4
description: Découvrez comment les modèles de texte T4 au moment de la conception vous permettent de générer du code de programme et d’autres fichiers dans votre projet Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8b7bc48a5c409dbecbb313fd277a31ad1cec287
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389135"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Génération de code durant la conception à l'aide de modèles de texte T4

Les modèles de texte T4 au moment de la conception vous permettent de générer du code de programme et d’autres fichiers dans votre projet Visual Studio. En général, vous écrivez les modèles afin qu’ils fassent varier le code qu’ils génèrent en fonction des données d’un *modèle*. Un modèle est un fichier ou une base de données qui contient des informations clés sur les exigences de votre application.

Par exemple, vous pourriez avoir un modèle qui définit un flux de travail sous la forme d'un tableau ou d'un diagramme. À partir du modèle, vous pouvez générer le logiciel qui exécute le flux de travail. Lorsque les besoins de vos utilisateurs changent, il est facile d’aborder le nouveau flux de travail avec les utilisateurs. La regénération du code à partir du flux de travail est plus fiable que la mise à jour manuelle du code.

> [!NOTE]
> Un *modèle* est une source de données qui décrit un aspect particulier d’une application. Il peut assumer n'importe quelle forme, dans n'importe quel genre de fichier ou de base de données. Il n’est pas obligatoire qu’il soit dans un format spécifique, tel qu’un modèle UML ou un modèle de langage spécifique à un domaine. Les modèles les plus courants assument la forme de tableaux ou de fichiers XML.

Vous connaissez sans doute déjà le concept de génération de code. Quand vous définissez des ressources dans un fichier **. resx** dans votre solution Visual Studio, un ensemble de classes et de méthodes est généré automatiquement. Le fichier de ressources simplifie et rend plus fiable la modification des ressources, par rapport à la modification manuelle des classes et des méthodes. Avec les modèles de texte, vous pouvez générer du code de la même façon à partir d'une source que vous avez conçue vous-même.

Un modèle de texte contient une combinaison du texte que vous souhaitez générer et du code de programme qui génère des parties variables du texte. Le code du programme vous permet de répéter ou d’omettre de manière conditionnelle des parties du texte généré. Le texte généré peut lui-même être du code de programme qui constituera une partie de votre application.

## <a name="create-a-design-time-t4-text-template"></a>Créer un Design-Time modèle de texte T4

1. Créez un projet Visual Studio ou ouvrez-en un existant.

2. Ajoutez un fichier de modèle de texte à votre projet et donnez-lui un nom avec l’extension **. TT**.

    Pour ce faire, dans **Explorateur de solutions**, dans le menu contextuel de votre projet, choisissez **Ajouter**  >  **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **modèle de texte** dans le volet central.

    Notez que la propriété **outil personnalisé** du fichier est **TextTemplatingFileGenerator**.

3. Ouvrez le fichier. Il contient déjà les directives suivantes :

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Si vous avez ajouté le modèle à un projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], l'attribut de langage est « `VB` ».

4. Ajoutez du texte à la fin du fichier. Par exemple :

   ```
   Hello, world!
   ```

5. Enregistrez le fichier .

    Vous pouvez voir un message d' **avertissement de sécurité** vous demandant de confirmer que vous souhaitez exécuter le modèle. Cliquez sur **OK**.

6. Dans **Explorateur de solutions**, développez le nœud du fichier de modèle et vous trouverez un fichier avec l’extension **.txt**. Ce fichier contient le texte généré à partir du modèle.

   > [!NOTE]
   > Si votre projet est un projet Visual Basic, vous devez cliquer sur **Afficher tous les fichiers** pour afficher le fichier de sortie.

### <a name="regenerate-the-code"></a>Régénérer le code

Un modèle est exécuté, générant le fichier auxiliaire, dans les cas suivants :

- Modifiez le modèle, puis passez au focus sur une autre fenêtre Visual Studio.

- Enregistrez le modèle.

- Cliquez sur **transformer tous les modèles** dans le menu **générer** . Cela permet de transformer tous les modèles dans la solution Visual Studio.

- Dans **Explorateur de solutions**, dans le menu contextuel de n’importe quel fichier, choisissez **exécuter un outil personnalisé**. Appliquez cette méthode pour transformer un sous-ensemble de modèles sélectionné.

Vous pouvez également configurer un projet Visual Studio afin que les modèles soient exécutés lorsque les fichiers de données qu’ils lisent ont changé. Pour plus d’informations, consultez [régénération automatique du code](#Regenerating).

## <a name="generate-variable-text"></a>Générer le texte de la variable

Les modèles de texte vous permettent d'utiliser du code de programme pour varier le contenu du fichier généré.

1. Modifiez le contenu du fichier `.tt` :

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Enregistrez le fichier .tt et inspectez de nouveau le fichier .txt généré. Il mentionne les carrés des chiffres de 0 à 10.

   Notez que les instructions sont placées entre des signes `<#...#>` et les expressions uniques entre des signes `<#=...#>`. Pour plus d’informations, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

   Si vous écrivez le code généré en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], la directive `template` doit contenir `language="VB"`. `"C#"` est la valeur par défaut.

## <a name="debugging-a-design-time-t4-text-template"></a>Débogage d'un modèle de texte T4 au moment de la conception

Pour déboguer un modèle de texte

- Insérez `debug="true"` dans la directive `template`. Exemple :

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Définissez des points d'arrêt dans le modèle comme vous le feriez pour du code ordinaire.

- Choisissez **déboguer le modèle T4** dans le menu contextuel du fichier de modèle de texte dans Explorateur de solutions.

   Le modèle s’exécute et s’arrête aux points d’arrêt. Vous pouvez examiner les variables et parcourir le code de manière normale.

> [!TIP]
> `debug="true"` rend le mappage du code généré plus précisément pour le modèle de texte, en insérant plus de directives de numérotation de ligne dans le code généré. Si vous ne le spécifiez pas, les points d'arrêt risquent d'arrêter l'exécution dans l'état incorrect.
>
> Mais vous pouvez laisser la clause dans la directive de modèle même quand vous ne déboguez pas. Cela ne provoque qu'une très faible dégradation des performances.

## <a name="generating-code-or-resources-for-your-solution"></a>Génération de code ou de ressources pour votre solution

Vous pouvez générer des fichiers programmes qui varient en fonction d'un modèle. Un modèle est une entrée telle qu'une base de données, un fichier de configuration, un modèle UML, un modèle DSL ou autre source. En général, vous générez plusieurs fichiers programme à partir du même modèle. Pour cela, vous devez créer un fichier de modèle pour chaque fichier programme généré et faire en sorte que tous les modèles lisent le même modèle.

### <a name="to-generate-program-code-or-resources"></a>Pour générer du code de programme ou des ressources

1. Modifiez la directive de sortie pour générer un fichier du type approprié, tel que .cs, .vb, .resx ou .xml.

2. Insérez du code qui générera le code de solution nécessaire. Par exemple, si vous souhaitez générer trois déclarations de champ de nombres entiers dans une classe :

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Enregistrez le fichier est inspectez le fichier généré, qui contient maintenant le code suivant :

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Génération de code et texte généré

Quand vous générez du code de programme, vous devez éviter toute confusion entre le code de génération qui s'exécute dans votre modèle et le code généré résultant qui devient partie intégrante de votre solution. Il n'est pas obligatoire que les deux langages soient identiques.

L'exemple précédent comporte deux versions. Dans une version, le code de génération est en C#. Dans l'autre version, le code de génération est en Visual Basic. Mais le texte généré par ces deux versions est identique et il s'agit d'une classe C#.

De la même manière, vous pourriez utiliser un modèle [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pour générer du code dans n'importe quel langage. Il n'est pas obligatoire que le texte généré soit dans un langage spécifique et il n'est pas obligatoire que ce soit du code de programme.

### <a name="structuring-text-templates"></a>Structuration des modèles de texte

Une meilleure pratique consiste à séparer le code de modèle en deux parties :

- Une partie configuration ou collecte de données, qui définit des valeurs dans des variables mais ne contient pas de blocs de texte. Dans l'exemple précédent, cette partie est l'initialisation de `properties`.

   On appelle parfois cette section la section « modèle », car elle construit un modèle en magasin et lit généralement un fichier de modèle.

- La partie génération de texte (`foreach(...){...}` dans l'exemple), qui utilise les valeurs des variables.

   Cette séparation n'est pas obligatoire, mais elle simplifie la lecture du modèle en réduisant la complexité de la partie qui comprend du texte.

## <a name="reading-files-or-other-sources"></a>Lecture de fichiers ou d'autres sources

Pour accéder à une base de données ou à un fichier de modèle, votre code de modèle peut utiliser des assemblys tels que System.XML. Pour pouvoir accéder à ces assemblys, vous devez insérer des directives telles que celles-ci :

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

La `assembly` directive met l’assembly spécifié à la disposition de votre code de modèle, de la même manière que la section des références d’un projet Visual Studio. Vous n'êtes pas obligé d'inclure une référence à System.dll, car il est référencé automatiquement. La directive `import` vous permet d'utiliser des types sans utiliser leurs noms qualifiés complets, de la même manière que la directive `using` dans un fichier programme ordinaire.

Par exemple, après l’importation de **System.IO**, vous pouvez écrire :

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Ouverture d’un fichier avec un nom de chemin d’accès relatif

Pour charger un fichier à partir d'un emplacement relatif au modèle de texte, vous pouvez utiliser `this.Host.ResolvePath()`. Pour utiliser this.Host, vous devez définir `hostspecific="true"` dans `template` :

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Ensuite, vous pouvez par exemple écrire :

```csharp
<# string filename = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim filename = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Vous pouvez aussi utiliser `this.Host.TemplateFile`, qui identifie le nom du fichier de modèle actuel.

Le type de `this.Host` (en VB, `Me.Host`) est `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Obtention de données à partir de Visual Studio

Pour utiliser les services fournis dans Visual Studio, définissez l' `hostSpecific` attribut et chargez l' `EnvDTE` assembly. Importation `Microsoft.VisualStudio.TextTemplating` , qui contient la `GetCOMService()` méthode d’extension.  Vous pouvez ensuite utiliser IServiceProvider.GetCOMService() pour accéder à DTE et d'autres services. Exemple :

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Un modèle de texte s'exécute dans son propre domaine d'application et les services sont accessibles par le marshaling. Dans cette circonstance, GetCOMService() est plus fiable que GetService().

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Régénération automatique du code

En général, plusieurs fichiers dans une solution Visual Studio sont générés avec un modèle d’entrée. Chaque fichier est généré à partir de son propre modèle, mais les modèles font tous référence au même modèle.

Si le modèle source change, vous devez réexécuter tous les modèles de la solution. Pour effectuer cette opération manuellement, choisissez **transformer tous les modèles** dans le menu **générer** .

Si vous avez installé le kit de développement logiciel (SDK) de modélisation Visual Studio, vous pouvez faire en sorte que tous les modèles soient transformés automatiquement chaque fois que vous effectuez une génération. Pour cela, modifiez votre fichier de projet (.csproj or .vbproj) dans un éditeur de texte et ajoutez les lignes suivantes vers la fin du fichier, après toute autre instruction `<import>` :

> [!NOTE]
> Le kit SDK de transformation de modèle de texte et le kit de développement logiciel (SDK) de modélisation Visual Studio sont installés automatiquement lorsque vous installez des fonctionnalités spécifiques de Visual Studio. Pour plus d’informations, consultez [ce billet de blog](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Pour plus d’informations, consultez [génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Envoie de rapports d’erreurs

Pour placer des messages d’erreur et d’avertissement dans la fenêtre d’erreur de Visual Studio, vous pouvez utiliser les méthodes suivantes :

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Conversion d’un fichier existant en modèle

L'un des avantages des modèles, c'est que leur apparence se rapproche des fichiers qu'ils génèrent, avec en plus du code de programme inséré. Cela nous suggère une méthode utile pour créer un modèle. Commencez par créer un fichier ordinaire en tant que prototype, tel qu’un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] fichier, puis introduisez progressivement du code de génération qui fait varier le fichier résultant.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Pour convertir un fichier existant en modèle au moment de la conception

1. À votre projet Visual Studio, ajoutez un fichier du type que vous souhaitez générer, tel qu’un `.cs` `.vb` fichier, ou `.resx` .

2. Testez le nouveau fichier pour vous assurer qu'il fonctionne.

3. Dans Explorateur de solutions, remplacez l’extension de nom de fichier par **. TT**.

4. Vérifiez les propriétés suivantes du fichier **. TT** :

   |Propriété |Paramètre |
   |-|-|
   | **Custom Tool =** | **TextTemplatingFileGenerator** |
   | **Build Action =** | **Aucun** |

5. Insérez les lignes suivantes au début du fichier :

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Si vous souhaitez écrire le code génération de votre modèle en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], affectez la valeur `language` au lieu de `"VB"` à l'attribut `"C#"`.

    Définissez l'attribut `extension` sur l'extension de nom de fichier correspondant au type de fichier que vous souhaitez générer, par exemple `.cs`, `.resx` ou `.xml`.

6. Enregistrez le fichier .

    Un fichier auxiliaire est créé, avec l’extension spécifiée. Ses propriétés sont correctes pour le type de fichier. Par exemple, la propriété **action de génération** d’un fichier. cs est **compiled**.

    Vérifiez que le contenu du fichier généré est identique à celui du fichier d'origine.

7. Identifiez une partie du fichier que vous souhaitez faire varier. Par exemple, une partie qui apparaît uniquement dans certaines conditions, qui est répétée ou dont les valeurs spécifiques varient. Insérez le code de génération. Enregistrez le fichier et vérifiez que le fichier auxiliaire est généré correctement. Répétez cette étape.

## <a name="guidelines-for-code-generation"></a>Instructions pour la génération de code

Veuillez consulter [les instructions relatives à l’écriture de modèles de texte T4](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Étapes suivantes

|Étape suivante|Rubrique|
|-|-|
|Écrire et déboguer un modèle de texte plus avancé, avec du code qui utilise des fonctions auxiliaires, des fichiers inclus et des données externes.|[Écriture d'un modèle de texte T4](../modeling/writing-a-t4-text-template.md)|
|Générer des documents à partir de modèles au moment de l'exécution.|[Génération de texte durant l'exécution à l'aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Exécutez la génération de texte en dehors de Visual Studio.|[Génération de fichiers avec l'utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformer vos données sous la forme d’un langage spécifique à un domaine.|[Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)|
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d'une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Voir aussi

- [Instructions relatives à l'écriture de modèles de texte T4](../modeling/guidelines-for-writing-t4-text-templates.md)
