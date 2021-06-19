---
title: Accès aux modèles depuis des modèles de texte
description: Découvrez comment vous pouvez utiliser des modèles de texte pour créer des fichiers de rapport, des fichiers de code source et d’autres fichiers texte basés sur des modèles de langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05e21dacfe56f41f1d2c0da51659ab55203db1a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389161"
---
# <a name="access-models-from-text-templates"></a>Accéder à des modèles à partir de modèles de texte

À l’aide de modèles de texte, vous pouvez créer des fichiers de rapport, des fichiers de code source et d’autres fichiers texte basés sur des modèles de langage spécifique à un domaine. Pour obtenir des informations de base sur les modèles de texte, consultez [génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md). Les modèles de texte fonctionnent en mode expérimental quand vous déboguez votre DSL, et ils fonctionnent également sur un ordinateur sur lequel vous avez déployé le DSL.

> [!NOTE]
> Lorsque vous créez une solution DSL, des exemples de fichiers de modèle de texte **\* . TT** sont générés dans le projet de débogage. Lorsque vous modifiez les noms des classes de domaine, ces modèles ne fonctionneront plus. Néanmoins, elles incluent les directives de base dont vous avez besoin, et fournissent des exemples que vous pouvez mettre à jour pour qu’ils correspondent à votre DSL.

 Pour accéder à un modèle à partir d’un modèle de texte :

- Affectez à la propriété inherit de la directive template la valeur [Microsoft. VisualStudio. TextTemplating. vshost. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). Cela permet d’accéder au magasin.

- Spécifiez les processeurs de directive pour le DSL auquel vous souhaitez accéder. Cela charge les assemblys de votre DSL afin que vous puissiez utiliser ses classes de domaine, leurs propriétés et leurs relations dans le code de votre modèle de texte. Il charge également le fichier de modèle que vous spécifiez.

  Un `.tt` fichier similaire à l’exemple suivant est créé dans le projet de débogage lorsque vous créez une nouvelle solution Visual Studio à partir du modèle de langage minimal DSL.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Notez les points suivants sur ce modèle :

- Le modèle peut utiliser les classes de domaine, les propriétés et les relations que vous avez définies dans la définition DSL.

- Le modèle charge le fichier de modèle que vous spécifiez dans la `requires` propriété.

- Une propriété dans `this` contient l’élément racine. À partir de là, votre code peut accéder à d’autres éléments du modèle. Le nom de la propriété est généralement identique à celui de la classe de domaine racine de votre DSL. Dans cet exemple, il s’agit de `this.ExampleModel`.

- Bien que le langage dans lequel les fragments de code sont écrits est C#, vous pouvez générer du texte de n’importe quel type. Vous pouvez également écrire le code dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en ajoutant la propriété `language="VB"` à la `template` directive.

- Pour déboguer le modèle, ajoutez `debug="true"` à la `template` directive. Le modèle s’ouvre dans une autre instance de Visual Studio si une exception se produit. Si vous souhaitez vous arrêter dans le débogueur à un point spécifique dans le code, insérez l’instruction `System.Diagnostics.Debugger.Break();`

   Pour plus d’informations, consultez [débogage d’un modèle de texte T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>À propos du processeur de directive DSL
 Le modèle peut utiliser les classes de domaine que vous avez définies dans votre définition DSL. Cela est dû à une directive qui apparaît généralement près du début du modèle. Dans l’exemple précédent, il s’agit de ce qui suit.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Le nom de la directive ( `MyLanguage` , dans cet exemple) est dérivé du nom de votre DSL. Il appelle un *processeur de directive* qui est généré dans le cadre de votre DSL. Vous pouvez trouver son code source dans **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Le processeur de directive DSL effectue deux tâches principales :

- Il insère efficacement des directives d’assembly et d’importation dans le modèle qui fait référence à votre DSL. Cela vous permet d’utiliser vos classes de domaine dans le code du modèle.

- Il charge le fichier que vous spécifiez dans le `requires` paramètre et définit une propriété dans `this` qui fait référence à l’élément racine du modèle chargé.

## <a name="validating-the-model-before-running-the-template"></a>Validation du modèle avant l’exécution du modèle
 Vous pouvez forcer la validation du modèle avant l’exécution du modèle.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Notez que :

1. Les `filename` `validation` paramètres et sont séparés par des « ; » et il ne doit pas y avoir d’autres séparateurs ou espaces.

2. La liste des catégories de validation détermine les méthodes de validation qui seront exécutées. Plusieurs catégories doivent être séparées par « &#124; » et il ne doit pas y avoir d’autres séparateurs ou espaces.

   Si une erreur est détectée, elle est signalée dans la fenêtre Erreurs et le fichier de résultats contient un message d’erreur.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Accès à plusieurs modèles à partir d’un modèle de texte

> [!NOTE]
> Cette méthode vous permet de lire plusieurs modèles dans le même modèle, mais ne prend pas en charge les références ModelBus. Pour lire les modèles qui sont liés par des références ModelBus, consultez [utilisation de Visual Studio Modelbus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Si vous souhaitez accéder à plusieurs modèles à partir du même modèle de texte, vous devez appeler le processeur de directive généré une fois pour chaque modèle. Vous devez spécifier le nom de fichier de chaque modèle dans le `requires` paramètre. Vous devez spécifier les noms que vous souhaitez utiliser pour la classe de domaine racine dans le `provides` paramètre. Vous devez spécifier des valeurs différentes pour les `provides` paramètres dans chaque appel de directive. Par exemple, supposons que vous avez trois fichiers de modèle appelés Library.xyz, School.xyz et Work.xyz. Pour y accéder à partir du même modèle de texte, vous devez écrire trois appels de directive qui ressemblent à ceux qui suivent.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Cet exemple de code est destiné à un langage basé sur le modèle de solution de langage minimal.

 Pour accéder aux modèles dans votre modèle de texte, vous pouvez maintenant écrire du code similaire au code de l’exemple suivant.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Chargement dynamique des modèles
 Si vous souhaitez déterminer au moment de l’exécution les modèles à charger, vous pouvez charger un fichier de modèle dynamiquement dans le code de votre programme, au lieu d’utiliser la directive spécifique à DSL.

 Toutefois, l’une des fonctions de la directive DSL spécifique consiste à importer l’espace de noms DSL, afin que le code du modèle puisse utiliser les classes de domaine définies dans ce DSL. Étant donné que vous n’utilisez pas la directive, vous devez ajouter **\<assembly>** **\<import>** des directives et pour tous les modèles que vous pouvez charger. C’est facile si les différents modèles que vous pouvez charger sont toutes des instances du même DSL.

 Pour charger le fichier, la méthode la plus efficace consiste à utiliser Visual Studio ModelBus. Dans un scénario classique, votre modèle de texte utilisera une directive DSL spécifique pour charger le premier modèle de la manière habituelle. Ce modèle contient des références ModelBus à un autre modèle. Vous pouvez utiliser ModelBus pour ouvrir le modèle référencé et accéder à un élément particulier. Pour plus d’informations, consultez [utilisation de Visual Studio Modelbus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Dans un scénario moins habituel, vous souhaiterez peut-être ouvrir un fichier de modèle pour lequel vous disposez uniquement d’un nom de fichier et qui ne figure peut-être pas dans le projet Visual Studio actuel. Dans ce cas, vous pouvez ouvrir le fichier à l’aide de la technique décrite dans [Comment : ouvrir un modèle à partir d’un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Génération de plusieurs fichiers à partir d’un modèle
 Si vous souhaitez générer plusieurs fichiers (par exemple, pour générer un fichier distinct pour chaque élément d’un modèle), il existe plusieurs approches possibles. Par défaut, un seul fichier est généré à partir de chaque fichier de modèle.

### <a name="splitting-a-long-file"></a>Fractionnement d’un fichier long
 Dans cette méthode, vous utilisez un modèle pour générer un seul fichier, séparé par un délimiteur. Vous fractionnez ensuite le fichier en plusieurs parties. Il existe deux modèles : un pour générer le fichier unique et l’autre pour le fractionner.

 **LoopTemplate. T4** génère le long fichier unique. Notez que son extension de fichier est « . T4 », car elle ne doit pas être traitée directement lorsque vous cliquez sur **transformer tous les modèles**. Ce modèle prend un paramètre qui spécifie la chaîne de délimiteur qui sépare les segments :

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` appelle `LoopTemplate.t4` , puis divise le fichier résultant en ses segments. Notez que ce modèle n’a pas besoin d’être un modèle de modélisation, car il ne lit pas le modèle.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```
