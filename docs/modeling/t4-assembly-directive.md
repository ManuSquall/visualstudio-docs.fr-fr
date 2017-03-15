---
title: "T4 Assembly Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 4
---
# T4 Assembly Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans un modèle de texte au moment du design [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directive `assembly` charge un assembly afin que votre code de modèle puisse utiliser ses types.  L'effet est semblable à l'ajout d'une référence d'assembly dans un projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Pour une vue d'ensemble de l'écriture de modèles de texte, consultez [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Vous n'avez pas besoin de la directive `assembly` dans un modèle de texte au moment de l'exécution \(prétraité\).  À la place, ajoutez les assemblys nécessaires aux **Références** de votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Utilisation de la directive d'assembly  
 La syntaxe de la directive est la suivante :  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Le nom d'assembly doit correspondre à l'un des éléments suivants :  
  
-   Nom fort d'un assembly dans le GAC, tel que `System.Xml.dll`.  Vous pouvez également utiliser la forme longue, telle que `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`.  Pour plus d'informations, consultez <xref:System.Reflection.AssemblyName>.  
  
-   Chemin d'accès absolu de l'assembly  
  
 Vous pouvez utiliser la syntaxe `$(variableName)` pour référencer des variables [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] telles que `$(SolutionDir)`, et `%VariableName%` pour référencer des variables d'environnement.  Par exemple :  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 La directive assembly n'a aucun effet dans un modèle de texte prétraité.  Incluez plutôt les références nécessaires dans la section **Références** de votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations, consultez [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Assemblys standard  
 Les assemblys suivants sont chargés automatiquement, afin que vous n'ayez pas besoin d'écrire des directives d'assembly pour eux :  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 Si vous utilisez une directive personnalisée, le processeur de directive peut charger des assemblys supplémentaires.  Par exemple, si vous écrivez des modèles pour un langage spécifique au domaine \(DSL\), vous n'avez pas besoin d'écrire des directives d'assembly pour les assemblys suivants :  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   Assembly contenant votre langage spécifique à un domaine.  
  
##  <a name="msbuild"></a> Utilisation des propriétés de projet dans MSBuild et Visual Studio  
 Les macros Visual Studio telles que $\(SolutionDir\) ne fonctionnent pas dans MSBuild.  Si vous souhaitez transformer les modèles de votre ordinateur de build, vous devez utiliser les propriétés de projet à la place.  
  
 Modifiez votre fichier projet .csproj ou .vbproj pour définir une propriété de projet.  Cet exemple définit une propriété nommée `myLibFolder` :  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Maintenant, vous pouvez utiliser votre propriété de projet dans les modèles de texte, lesquels se transforment correctement dans Visual Studio et MSBuild :  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## Voir aussi  
 [T4 Include Directive](../modeling/t4-include-directive.md)