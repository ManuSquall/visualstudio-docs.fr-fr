---
title: "Méthodes utilitaires de modèle de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66b4c44a79446aacc56761b6b565d8c979d007f7
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="text-template-utility-methods"></a>Méthodes utilitaires de modèle de texte

Il existe plusieurs méthodes qui sont toujours disponibles pour vous lorsque vous écrivez du code dans un modèle de texte Visual Studio. Ces méthodes sont définies dans <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Vous pouvez également utiliser d’autres méthodes et les services fournis par l’environnement d’hôte dans un modèle de texte (non prétraité) normal. Par exemple, vous pouvez résoudre les chemins d’accès de fichier, consigner les erreurs et obtenir des services fournis par Visual Studio et les packages chargés. Pour plus d’informations, consultez [l’accès à Visual Studio à partir d’un modèle de texte](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).
  
## <a name="write-methods"></a>Écrire des méthodes

Vous pouvez utiliser la `Write()` et `WriteLine()` méthodes pour ajouter du texte à l’intérieur d’un bloc de code standard, au lieu d’utiliser un bloc de code expression. Les blocs de deux fichiers de code suivantes sont équivalentes.  
  
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
  
### <a name="code-block-using-writeline"></a>Bloc de code à l’aide de WriteLine()  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Il peut s’avérer utile d’utiliser une de ces méthodes utilitaires au lieu d’un bloc d’expression à l’intérieur d’un bloc de code long avec les structures de contrôle imbriquées.  
  
 Le `Write()` et `WriteLine()` méthodes ont deux surcharges, l’une qui prend un paramètre de chaîne unique et l’autre qui prend une chaîne de format composite ainsi qu’un tableau d’objets à inclure dans la chaîne (comme la `Console.WriteLine()` méthode). Les deux utilisations suivantes de `WriteLine()` sont fonctionnellement équivalents :  
  
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

 Vous pouvez utiliser des méthodes de mise en retrait pour mettre en forme la sortie de votre modèle de texte. Le <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> classe a un `CurrentIndent` propriété qui indique la mise en retrait actuelle dans le modèle de texte de chaîne et un `indentLengths` champ qui est une liste des mises en retrait qui ont été ajoutés. Vous pouvez ajouter une mise en retrait avec le `PushIndent()` (méthode) et soustraire une mise en retrait avec le `PopIndent()` (méthode). Si vous souhaitez supprimer tous les retraits, utilisez le `ClearIndent()` (méthode). Le bloc de code suivant illustre l’utilisation de ces méthodes :  
  
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
  
 Ce bloc de code génère la sortie suivante :  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>Méthodes d’erreur et avertissement  
 Vous pouvez utiliser des méthodes d’erreur et avertissement utilitaire pour ajouter des messages à la liste d’erreurs Visual Studio. Par exemple, le code suivant ajouterez un message d’erreur à la liste d’erreurs.  
  
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
  
## <a name="access-to-host-and-service-provider"></a>Accès à l’hôte et le fournisseur de services  
 La propriété `this.Host` fournir l’accès aux propriétés exposées par l’hôte qui exécute le modèle. Pour utiliser `this.Host`, vous devez définir `hostspecific` l’attribut dans la `<@template#>` directive :  
  
 `<#@template ... hostspecific="true" #>`  
  
 Le type de `this.Host` dépend du type d’hôte dans lequel le modèle s’exécute. Dans un modèle qui s’exécute dans Visual Studio, vous pouvez effectuer un cast `this.Host` à `IServiceProvider` pour accéder aux services tels que l’IDE. Exemple :  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>À l’aide d’un autre ensemble de méthodes utilitaires  
 Dans le cadre du processus de génération de texte, votre fichier de modèle est transformé en une classe, qui est toujours nommée `GeneratedTextTransformation`et hérite de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Si vous souhaitez utiliser un autre ensemble de méthodes au lieu de cela, vous pouvez écrire votre propre classe et le spécifier dans la directive de modèle. Votre classe doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Utilisez la `assembly` directive pour référencer l’assembly où se trouve la classe compilée.