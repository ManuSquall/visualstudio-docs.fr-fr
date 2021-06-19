---
title: Méthodes utilitaires de modèle de texte
description: Découvrez les différentes méthodes utilitaires de modèle de texte qui sont à votre disposition lorsque vous écrivez du code dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b45bf6418562da5315c986a64a1295c137e982d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388683"
---
# <a name="text-template-utility-methods"></a>Méthodes utilitaires de modèle de texte

Il existe plusieurs méthodes qui sont toujours à votre disposition lorsque vous écrivez du code dans un modèle de texte Visual Studio. Ces méthodes sont définies dans <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Vous pouvez également utiliser d’autres méthodes et services fournis par l’environnement hôte dans un modèle de texte normal (non prétraité). Par exemple, vous pouvez résoudre les chemins d’accès aux fichiers, consigner les erreurs et obtenir les services fournis par Visual Studio, ainsi que tous les packages chargés. Pour plus d’informations, consultez [accès à Visual Studio à partir d’un modèle de texte](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Méthodes d’écriture

Vous pouvez utiliser les `Write()` `WriteLine()` méthodes et pour ajouter du texte à l’intérieur d’un bloc de code standard au lieu d’utiliser un bloc de code d’expression. Les deux blocs de code suivants sont fonctionnellement équivalents.

### <a name="code-block-with-an-expression-block"></a>Bloc de code avec un bloc d’expression

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Bloc de code à l’aide de WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Il peut s’avérer utile d’utiliser l’une de ces méthodes utilitaires au lieu d’un bloc d’expression à l’intérieur d’un bloc de code long avec des structures de contrôle imbriquées.

Les `Write()` `WriteLine()` méthodes et ont deux surcharges, une qui prend un paramètre de chaîne unique et une chaîne de format composite plus un tableau d’objets à inclure dans la chaîne (comme la `Console.WriteLine()` méthode). Les deux utilisations suivantes de `WriteLine()` sont fonctionnellement équivalentes :

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Méthodes de mise en retrait

Vous pouvez utiliser des méthodes de mise en retrait pour mettre en forme la sortie de votre modèle de texte. La <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> classe a une `CurrentIndent` propriété de type chaîne qui indique la mise en retrait actuelle dans le modèle de texte et un `indentLengths` champ qui est une liste des mises en retrait qui ont été ajoutées. Vous pouvez ajouter une mise en retrait avec la `PushIndent()` méthode et soustraire une mise en retrait à la `PopIndent()` méthode. Si vous souhaitez supprimer toutes les mises en retrait, utilisez la `ClearIndent()` méthode. Le bloc de code suivant illustre l’utilisation de ces méthodes :

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Ce bloc de code produit la sortie suivante :

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Méthodes d’erreur et d’avertissement

Vous pouvez utiliser les méthodes de l’utilitaire d’erreur et d’avertissement pour ajouter des messages au Liste d’erreurs Visual Studio. Par exemple, le code suivant ajoute un message d’erreur à l’Liste d’erreurs.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Accès à l’hôte et au fournisseur de services

La propriété `this.Host` peut fournir l’accès aux propriétés exposées par l’hôte qui exécute le modèle. Pour utiliser `this.Host` , vous devez définir `hostspecific` l’attribut dans la `<@template#>` directive :

`<#@template ... hostspecific="true" #>`

Le type de `this.Host` dépend du type d’hôte dans lequel le modèle est en cours d’exécution. Dans un modèle qui s’exécute dans Visual Studio, vous pouvez effectuer un cast vers pour accéder `this.Host` `IServiceProvider` à des services tels que l’IDE. Exemple :

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Utilisation d’un autre ensemble de méthodes utilitaires

Dans le cadre du processus de génération de texte, votre fichier de modèle est transformé en une classe, qui est toujours nommée `GeneratedTextTransformation` et hérite de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Si vous souhaitez utiliser un autre ensemble de méthodes, vous pouvez écrire votre propre classe et la spécifier dans la directive de modèle. Votre classe doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Utilisez la `assembly` directive pour référencer l’assembly où se trouve la classe compilée.
