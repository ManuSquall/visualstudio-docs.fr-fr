---
title: "Text Template Utility Methods | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, utility methods"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 50
---
# Text Template Utility Methods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous disposez toujours de plusieurs méthodes lorsque vous écrivez du code dans un modèle de texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Ces méthodes sont définies dans <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Vous pouvez également utiliser d'autres méthodes et services fournis par l'environnement d'hôte dans un modèle de texte normal \(non prétraité\).  Par exemple, vous pouvez résoudre des chemins d'accès de fichier, enregistrer des erreurs et obtenir des services fournis par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et tous les packages chargés.  Pour plus d'informations, consultez [Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/fr-fr/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## Méthodes Write  
 Vous pouvez utiliser les méthodes `Write()` et `WriteLine()` pour ajouter du texte dans un bloc de code standard, au lieu d'employer un bloc de code d'expression.  Les deux blocs de code suivants sont équivalents du point de vue fonctionnel.  
  
##### Bloc de code avec un bloc d'expression  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### Bloc de code utilisant WriteLine\(\)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Il peut s'avérer utile d'employer l'une de ces méthodes utilitaires au lieu d'un bloc d'expression dans un bloc de code long comportant des structures de contrôle imbriquées.  
  
 Les méthodes `Write()` et `WriteLine()` ont deux surcharges, l'une acceptant un paramètre de chaîne unique et l'autre acceptant une chaîne de format composite, ainsi qu'un tableau d'objets à inclure dans la chaîne \(comme la méthode `Console.WriteLine()`\).  Les deux utilisations suivantes de `WriteLine()` sont équivalentes du point de vue fonctionnel :  
  
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
  
## Méthodes de mise en retrait  
 Vous pouvez utiliser des méthodes de mise en retrait pour mettre en forme la sortie de votre modèle de texte.  La classe <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> a une propriété de type chaîne `CurrentIndent` qui montre la mise en retrait actuelle dans le modèle de texte et un champ `indentLengths` qui correspond à une liste des mises en retrait ajoutées.  Vous pouvez ajouter une mise en retrait avec la méthode `PushIndent()` et soustraire une mise en retrait avec la méthode `PopIndent()`.  Si vous voulez supprimer toutes les mises en retrait, utilisez la méthode `ClearIndent()`.  Le bloc de code suivant illustre l'utilisation de ces méthodes :  
  
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
  
## Méthodes d'erreur et d'avertissement  
 Vous pouvez utiliser des méthodes utilitaires d'erreur et d'avertissement pour ajouter des messages à la liste d'erreurs de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Par exemple, le code suivant ajoutera un message d'erreur à la liste d'erreurs.  
  
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
  
## Accès à l'hôte et au fournisseur de services  
 La propriété `this.Host` peut donner accès aux propriétés exposées par l'hôte qui exécute le modèle.  Pour utiliser `this.Host`, vous devez définir l'attribut `hostspecific` dans la directive `<@template#>` :  
  
 `<#@template ...  hostspecific="true" #>`  
  
 Le type de `this.Host` dépend du type d'hôte dans lequel le modèle s'exécute.  Dans un modèle qui s'exécute dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez effectuer un cast de `this.Host` en `IServiceProvider` pour accéder à des services tels que l'IDE.  Par exemple :  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## Utilisation d'un autre ensemble de méthodes utilitaires  
 Dans le cadre du processus de génération de texte, votre fichier modèle est transformé en classe, qui est toujours nommée `GeneratedTextTransformation` et hérite de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  Si vous voulez utiliser à la place un autre ensemble de méthodes, vous pouvez écrire votre propre classe et la spécifier dans la directive de modèle.  Votre classe doit hériter de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Utilisez la directive `assembly` pour référencer l'assembly où se trouve la classe compilée.