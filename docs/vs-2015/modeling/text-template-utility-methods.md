---
title: Méthodes utilitaires de modèle de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658523"
---
# <a name="text-template-utility-methods"></a>Méthodes utilitaires de modèle de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il existe plusieurs méthodes qui sont toujours à votre disposition lorsque vous écrivez du code dans un modèle de texte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ces méthodes sont définies dans <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Vous pouvez également utiliser d’autres méthodes et services fournis par l’environnement hôte dans un modèle de texte normal (non prétraité). Par exemple, vous pouvez résoudre les chemins d’accès aux fichiers, consigner les erreurs et obtenir les services fournis par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et tous les packages chargés.  Pour plus d’informations, consultez [accès à Visual Studio à partir d’un modèle de texte](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Méthodes d’écriture
 Vous pouvez utiliser les méthodes `Write()` et `WriteLine()` pour ajouter du texte à l’intérieur d’un bloc de code standard au lieu d’utiliser un bloc de code d’expression. Les deux blocs de code suivants sont fonctionnellement équivalents.

##### <a name="code-block-with-an-expression-block"></a>Bloc de code avec un bloc d’expression

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

##### <a name="code-block-using-writeline"></a>Bloc de code à l’aide de WriteLine ()

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

 Les méthodes `Write()` et `WriteLine()` ont deux surcharges, une qui prend un paramètre de chaîne unique et une chaîne de format composite, ainsi qu’un tableau d’objets à inclure dans la chaîne (par exemple, la méthode `Console.WriteLine()`). Les deux utilisations suivantes de `WriteLine()` sont fonctionnellement équivalentes :

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
 Vous pouvez utiliser des méthodes de mise en retrait pour mettre en forme la sortie de votre modèle de texte. La classe <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> a une propriété de chaîne `CurrentIndent` qui indique la mise en retrait actuelle dans le modèle de texte et un champ `indentLengths` qui est une liste des mises en retrait qui ont été ajoutées. Vous pouvez ajouter une mise en retrait à l’aide de la méthode `PushIndent()` et soustraire une mise en retrait à la méthode `PopIndent()`. Si vous souhaitez supprimer toutes les mises en retrait, utilisez la méthode `ClearIndent()`. Le bloc de code suivant illustre l’utilisation de ces méthodes :

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
 Vous pouvez utiliser les méthodes de l’utilitaire d’erreur et d’avertissement pour ajouter des messages au Liste d’erreurs [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Par exemple, le code suivant ajoute un message d’erreur à l’Liste d’erreurs.

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
 La propriété `this.Host` peut fournir l’accès aux propriétés exposées par l’hôte qui exécute le modèle. Pour utiliser `this.Host`, vous devez définir `hostspecific` attribut dans la directive `<@template#>` :

 `<#@template ... hostspecific="true" #>`

 Le type de `this.Host` dépend du type d’hôte dans lequel le modèle s’exécute. Dans un modèle qui s’exécute dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez effectuer un cast `this.Host` en `IServiceProvider` pour accéder à des services tels que l’IDE. Exemple :

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Utilisation d’un autre ensemble de méthodes utilitaires
 Dans le cadre du processus de génération de texte, votre fichier de modèle est transformé en une classe, qui est toujours nommée `GeneratedTextTransformation`and hérite de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Si vous souhaitez utiliser un autre ensemble de méthodes, vous pouvez écrire votre propre classe et la spécifier dans la directive de modèle. Votre classe doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

 Utilisez la directive `assembly` pour référencer l’assembly où se trouve la classe compilée.
