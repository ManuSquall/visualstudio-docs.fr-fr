---
title: Blocs de contrôle des modèles de texte
description: En savoir plus sur les blocs de contrôle de modèle de texte et la façon dont les blocs de contrôle vous permettent d’écrire du code dans votre modèle de texte afin de faire varier la sortie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90a4efea7d37b83d3d5ff7a085abcf3439d99263
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388722"
---
# <a name="text-template-control-blocks"></a>Blocs de contrôle des modèles de texte
Les blocs de contrôle vous permettent d'écrire du code dans votre modèle de texte pour faire varier la sortie. Il existe trois types de blocs de contrôle, distingués par leurs crochets d'ouverture :

- `<# Standard control blocks #>` peut contenir des instructions.

- `<#= Expression control blocks #>` peut contenir des expressions.

- `<#+ Class feature control blocks #>` peut contenir des méthodes, des propriétés et des champs.

## <a name="standard-control-block"></a>Bloc de contrôle standard
 Les blocs de contrôle standard contiennent des instructions. Par exemple, le bloc standard suivant obtient les noms de tous les attributs du document XML :

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Vous pouvez incorporer du texte brut dans une instruction composée comme `if` ou `for`. Par exemple, ce fragment génère une ligne de sortie dans chaque itération de boucle :

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> Toujours utiliser {...} pour délimiter les instructions imbriquées qui contiennent du texte brut incorporé. L'exemple suivant peut ne pas fonctionner correctement :
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> À la place, vous devez inclure des {accolades}, comme suit :

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>Bloc de contrôle d'expression
 Les blocs de contrôle d'expression sont utilisés pour le code qui fournit des chaînes à écrire dans le fichier de sortie. Par exemple, avec l'exemple ci-dessus, vous pouvez imprimer les noms des attributs dans le fichier de sortie en modifiant le bloc de code comme suit :

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Bloc de contrôle de fonctionnalité de classe
 Vous pouvez utiliser des blocs de contrôle de fonctionnalité de classe pour ajouter des méthodes, des propriétés, des champs ou même des classes imbriquées à votre modèle de texte. Les blocs de fonctionnalité de classe sont le plus souvent utilisés pour fournir des fonctions d’assistance pour le code dans d’autres parties du modèle de texte. Par exemple, le bloc de fonctionnalité de classe suivant met en majuscule la première lettre du nom de l'attribut (ou la première lettre de chaque mot si le nom contient un espace blanc) :

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> Un bloc de contrôle de fonctionnalité de classe ne doit pas être suivi de blocs de contrôle standard dans le même fichier modèle. Toutefois, cette restriction ne s'applique pas au résultat de l'utilisation de directives `<#@include#>`. Chaque fichier inclus peut avoir des blocs standard suivis de blocs de fonctionnalité de classe.

 Vous pouvez créer une fonction qui génère une sortie en incorporant des blocs de texte et d'expression dans un bloc de contrôle de fonctionnalité de classe. Exemple :

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Vous pouvez appeler cette fonction à partir d'un bloc standard ou d'un autre bloc de fonctionnalité de classe :

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Comment utiliser les blocs de contrôle
 Tout le code contenu dans chacun des blocs de contrôle d'expression et standard d'un modèle unique (y compris celui figurant dans les modèles inclus) est combiné pour former la méthode `TransformText()` du code généré. (Pour plus d’informations sur l’inclusion d’autres modèles de texte avec la `include` directive, consultez Directives pour les modèles de [texte T4](../modeling/t4-text-template-directives.md).)

 Vous devez tenir compte des considérations suivantes quand vous utilisez des blocs de contrôle :

- **Langue.** Vous pouvez utiliser du code C# ou Visual Basic dans un modèle de texte. Le langage par défaut est C#, mais vous pouvez spécifier Visual Basic avec le paramètre `language` de la directive `template`. (Pour plus d’informations sur la `template` directive, consultez directives relatives aux [modèles de texte T4](../modeling/t4-text-template-directives.md).)

     Le langage que vous utilisez dans les blocs de contrôle n'a aucun rapport avec le langage ou le format du texte que vous générez dans un modèle de texte. Vous pouvez générer du code C# en utilisant du code Visual Basic ou vice versa.

     Vous ne pouvez utiliser qu'un seul langage dans un modèle de texte donné, y compris tous les modèles de texte que vous incluez avec la directive `include`.

- **Variables locales.** Étant donné que tout le code des blocs de contrôle d'expression et standard d'un modèle de texte est généré sous la forme d'une méthode unique, vous devez vérifier qu'il n'existe aucun conflit avec les noms des variables locales. Si vous incluez d'autres modèles de texte, vous devez vous assurer que les noms de variables sont uniques pour tous les modèles inclus. Pour ce faire, une méthode consiste à ajouter à chaque nom de variable locale une chaîne identifiant le modèle de texte dans lequel il a été déclaré.

     Nous vous recommandons également d'initialiser vos variables locales à des valeurs sensibles quand vous les déclarez, en particulier quand vous incluez plusieurs modèles de texte.

- **Imbrication de blocs de contrôle.** Les blocs de contrôle ne peuvent pas être imbriqués les uns dans les autres. Vous devez toujours terminer un bloc de contrôle donné avant d'en ouvrir un autre. Par exemple, le code suivant montre comment imprimer du texte d'un bloc d'expression dans le cadre d'un bloc de contrôle standard.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refactorisation.** Pour que vos modèles de texte restent courts et faciles à comprendre, nous vous recommandons fortement d'éviter d'employer du code répétitif en factorisant le code réutilisable au sein de fonctions d'assistance dans des blocs de fonctionnalité de classe ou en créant votre propre classe de modèle de texte qui hérite de la classe Microsoft.VisualStudio.TextTemplating.TextTransformation.
