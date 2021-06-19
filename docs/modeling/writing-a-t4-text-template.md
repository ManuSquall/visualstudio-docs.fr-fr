---
title: Écriture d'un modèle de texte T4
description: Découvrez les modèles de texte T4 et comment écrire un modèle de texte qui comprend des directives, des blocs de texte et des blocs de contrôle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8034e0d1df6410c842f7d93a4ee3023957904744
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388085"
---
# <a name="writing-a-t4-text-template"></a>Écriture d'un modèle de texte T4
Un modèle de texte contient le texte qui sera généré à partir du modèle. Par exemple, un modèle qui crée une page Web contiendra « \<html> ... » et toutes les autres parties standard d’une page HTML. Les *blocs de contrôle*, qui sont des fragments de code de programme, sont insérés dans le modèle. Les blocs de contrôle fournissent des valeurs variables et permettent à certaines parties du texte d'être conditionnelles et répétées.

 Cette structure simplifie le développement de modèle, car vous pouvez commencer avec un prototype du fichier généré et insérer de manière incrémentielle des blocs de contrôle qui font varier le résultat.

 Les modèles de texte sont formés des composants suivants :

- **Directives** : éléments qui contrôlent la façon dont le modèle est traité.

- **Blocs de texte** : contenu copié directement dans la sortie.

- **Blocs de contrôle** : code de programme qui insère des valeurs de variables dans le texte et contrôle des parties conditionnelles ou répétées du texte.

Pour tester les exemples de cette rubrique, copiez-les dans un fichier de modèle, comme décrit dans [génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Après avoir modifié le fichier de modèle, enregistrez-le, puis examinez le fichier de **.txt** de sortie.

## <a name="directives"></a>Directives
 Les directives de modèle de texte fournissent des instructions générales au moteur de création de modèles de texte concernant la manière de générer le code de transformation et le fichier de sortie.

 Par exemple, la directive suivante spécifie que le fichier de sortie doit avoir une extension .txt :

```
<#@ output extension=".txt" #>
```

 Pour plus d’informations sur les directives, consultez Directives pour les [modèles de texte T4](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Blocs de texte
 Un bloc de texte insère du texte directement dans le fichier de sortie. Il n'y a aucune mise en forme spéciale pour les blocs de texte. Par exemple, le modèle de texte suivant produit un fichier texte qui contient le mot « Hello » :

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Blocs de contrôle
 Les blocs de contrôle sont des sections de code de programme qui servent à transformer les modèles. Le langage par défaut est C#, mais pour utiliser [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] vous pouvez écrire cette directive au début du fichier :

```
<#@ template language="VB" #>
```

 Le langage dans lequel vous écrivez le code dans les blocs de contrôle est sans rapport avec la langue du texte généré.

### <a name="standard-control-blocks"></a>Blocs de contrôle standard
 Un bloc de contrôle standard est une section de code de programme qui génère une partie du fichier de sortie.

 Vous pouvez combiner autant de blocs de texte et de blocs de contrôle standard que vous le souhaitez dans un fichier de modèle. Toutefois, vous ne pouvez pas placer un bloc de contrôle dans un autre. Chaque bloc de contrôle standard est délimité par les symboles `<# ... #>`.

 Par exemple, le bloc de contrôle et le bloc de texte suivants font en sorte que le fichier de sortie contienne la ligne « 0, 1, 2, 3, 4 Hello! ».

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Au lieu d'utiliser des instructions `Write()` explicites, vous pouvez entrelacer du texte et du code. L’exemple suivant imprime « Hello ! » quatre fois :

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Vous pouvez insérer un bloc de texte partout où une instruction `Write();` serait autorisée dans le code.

> [!NOTE]
> Quand vous incorporez un bloc de texte dans une instruction composée telle qu’une boucle ou une condition conditionnelle, utilisez toujours les accolades {...} pour contenir le bloc de texte.

### <a name="expression-control-blocks"></a>Blocs de contrôle d'expression
 Un bloc de contrôle d'expression évalue une expression et la convertit en chaîne. Celle-ci est insérée dans le fichier de sortie.

 Les blocs de contrôle d'expression sont délimités par les symboles `<#= ... #>`.

 Par exemple, le bloc de contrôle suivant fait en sorte que le fichier de sortie contienne « 5 » :

```
<#= 2 + 3 #>
```

 Notez que le symbole d’ouverture comporte trois caractères « < # = ».

 L'expression peut inclure toute variable qui est dans la portée. Par exemple, ce bloc imprime des lignes avec des nombres :

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Bloc de contrôle de fonctionnalité de classe
 Un bloc de contrôle de fonctionnalité de classe définit des propriétés, des méthodes ou tout autre code qui ne doit pas être inclus dans la transformation principale. Les blocs de fonctionnalité de classe sont fréquemment utilisés pour les fonctions d'assistance.  En règle générale, les blocs de fonctionnalité de classe sont placés dans des fichiers séparés afin de pouvoir être [inclus](#Include) dans plusieurs modèles de texte.

 Les blocs de fonctionnalité de classe sont délimités par les symboles `<#+ ... #>`.

 Par exemple, le fichier de modèle suivant déclare et utilise une méthode :

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Les fonctionnalités de classe doivent être placées à la fin du fichier dans lequel elles sont écrites. Toutefois, vous pouvez inclure (`<#@include#>`) un fichier qui contient une fonctionnalité de classe, même si la directive `include` est suivie de texte et de blocs ordinaires.

 Pour plus d’informations sur les blocs de contrôle, consultez [blocs de contrôle de modèle de texte](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Les blocs de fonctionnalité de classe peuvent contenir des blocs de texte
 Vous pouvez écrire une méthode qui génère du texte. Exemple :

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Il est particulièrement utile de placer une méthode qui génère du texte dans un fichier distinct pouvant être inclus par plusieurs modèles.

## <a name="using-external-definitions"></a>Utilisation de définitions externes

### <a name="assemblies"></a>Assemblys
 Les blocs de code de votre modèle peuvent utiliser des types définis par les assemblys .NET les plus fréquemment utilisés tels que System.dll. De plus, vous pouvez faire référence à d'autres assemblys .NET ou à vos propres assemblys. Vous pouvez fournir un nom de chemin d’accès ou le nom fort d’un assembly :

```
<#@ assembly name="System.Xml" #>
```

 Vous devez utiliser des noms de chemins d’accès absolus ou des noms de macros standard dans le nom du chemin d’accès. Exemple :

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 La directive assembly n’a aucun effet dans un [modèle de texte prétraité](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Pour plus d’informations, consultez [directive d’assembly T4](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Espaces de noms
 La directive import est identique à la clause `using` en C# ou à la clause `imports` en Visual Basic. Elle vous permet de faire référence à des types dans votre code sans utiliser de nom qualifié complet :

```
<#@ import namespace="System.Xml" #>
```

 Vous pouvez utiliser autant de directives `assembly` et `import` que vous le souhaitez. Vous devez les placer avant les blocs de contrôle et de texte.

 Pour plus d’informations, consultez [directive import T4](../modeling/t4-import-directive.md).

### <a name="including-code-and-text"></a><a name="Include"></a> Inclusion de code et de texte
 La directive `include` insère du texte à partir d'un autre fichier de modèle. Par exemple, cette directive insère le contenu de `test.txt`.

```
<#@ include file="c:\test.txt" #>
```

 Le contenu inclus est traité presque comme s'il faisait partie du modèle de texte d'inclusion. Toutefois, vous pouvez inclure un fichier qui contient un bloc de fonctionnalité de classe `<#+...#>` même si la directive include est suivie de texte ordinaire et de blocs de contrôle standard.

 Pour plus d’informations, consultez [directive include T4](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Méthodes utilitaires
 Il existe plusieurs méthodes telles que `Write()` qui sont toujours disponibles dans un bloc de contrôle. Il s'agit notamment de méthodes destinées à vous aider à mettre en retrait la sortie et à signaler les erreurs.

 Vous pouvez aussi écrire votre propre jeu de méthodes utilitaires.

 Pour plus d’informations, consultez Méthodes de l' [utilitaire de modèle de texte](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Transformation de données et de modèles
 L'application la plus utile pour un modèle de texte consiste à générer une sortie basée sur le contenu d'une source telle qu'un modèle, une base de données ou un fichier de données. Votre modèle extrait et modifie la mise en forme des données. Une collection de modèles peut transformer une telle source en plusieurs fichiers.

 Il existe plusieurs approches pour la lecture du fichier source.

 **Lire un fichier dans le modèle de texte**. C'est le moyen le plus simple d'insérer des données dans le modèle :

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Chargez un fichier en tant que modèle navigable**. Une méthode plus puissante consiste à lire les données en tant que modèle navigable par votre code de modèle de texte. Par exemple, vous pouvez charger un fichier XML et le parcourir avec des expressions XPath. Vous pouvez également utiliser [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) pour créer un ensemble de classes avec lequel vous pouvez lire les données XML.

 **Modifiez le fichier de modèle dans un diagramme ou un formulaire.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] fournit des outils qui vous permettent de modifier un modèle en tant que diagramme ou formulaire Windows. Il est ainsi plus facile de discuter du modèle avec les utilisateurs de l'application générée. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] crée également un ensemble de classes fortement typées qui reflètent la structure du modèle. Pour plus d’informations, consultez [génération de code à partir d’un langage de Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Chemins d’accès de fichiers relatifs dans les modèles au moment du design
 Dans un [modèle de texte au moment du design](../modeling/design-time-code-generation-by-using-t4-text-templates.md), si vous souhaitez faire référence à un fichier à un emplacement relatif au modèle de texte, utilisez `this.Host.ResolvePath()` . Vous devez aussi définir `hostspecific="true"` dans la directive `template` :

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

Vous pouvez également obtenir d'autres services fournis par l'hôte. Pour plus d’informations, consultez [accès à Visual Studio ou à d’autres ordinateurs hôtes à partir d’un modèle](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Modèles de texte au moment du design exécutés dans un AppDomain distinct

 Vous devez savoir qu’un [modèle de texte au moment du design](../modeling/design-time-code-generation-by-using-t4-text-templates.md) s’exécute dans un AppDomain qui est distinct de l’application principale. Dans la plupart des cas cela n'est pas important, mais dans certains cas complexes certaines restrictions peuvent s'appliquer. Par exemple, si vous souhaitez passer des données dans le modèle ou en dehors de celui-ci à partir d'un service distinct, ce service doit fournir une API sérialisable.

 (Ce n’est pas le cas d’un [modèle de texte au moment](../modeling/run-time-text-generation-with-t4-text-templates.md)de l’exécution, qui fournit du code compilé avec le reste de votre code.)

## <a name="editing-templates"></a>Modification de modèles
 Vous pouvez télécharger des éditeurs de modèle de texte spécialisés à partir de la galerie en ligne du Gestionnaire d'extensions. Dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**. Cliquez sur **Galerie en ligne**, puis utilisez l’outil de recherche.

## <a name="related-topics"></a>Rubriques connexes

|Tâche|Rubrique|
|-|-|
|Écrire un modèle.|[Instructions relatives à l'écriture de modèles de texte T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Générer du texte à l'aide de code de programme.|[Structure du modèle de texte](../modeling/writing-a-t4-text-template.md)|
|Générer des fichiers dans une solution Visual Studio.|[Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Exécutez la génération de texte en dehors de Visual Studio.|[Génération de fichiers avec l'utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformer vos données sous la forme d’un langage spécifique à un domaine.|[Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)|
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d'une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|
