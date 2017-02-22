---
title: "How to: Extend the Visual Studio Build Process | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, overriding predefined targets"
  - "MSBuild, overriding DependsOn properties"
  - "MSBuild, extending Visual Studio builds"
  - "MSBuild, DependsOn properties"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Extend the Visual Studio Build Process
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le processus de génération [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est défini par une série de fichiers [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].targets qui sont importés dans votre fichier projet.  L'un de ces fichiers importés, Microsoft.Common.targets, peut être étendu pour vous permettre d'exécuter des tâches personnalisées à plusieurs points du processus de génération.  Cette rubrique présente deux méthodes permettant d'étendre le processus de génération [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] :  
  
-   Substitution de cibles prédéfinies spécifiques définies dans Microsoft.Common.targets.  
  
-   Substitution des propriétés « DependsOn » définies dans Microsoft.Common.targets.  
  
## Substitution de cibles prédéfinies  
 Le fichier Microsoft.Common.targets contient un jeu de cibles vides prédéfinies qui sont appelées avant et après certaines des cibles majeures du processus de génération.  Par exemple, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] appelle la cible `BeforeBuild` avant la cible `CoreBuild` principale et la cible `AfterBuild` après la cible `CoreBuild`.  Par défaut, les cibles vides de Microsoft.Common.targets n'ont aucun effet, mais vous pouvez remplacer leur comportement par défaut en définissant les cibles souhaitées dans un fichier projet qui importe Microsoft.Common.targets.  Vous avez ainsi la possibilité d'utiliser des tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour mieux contrôler le processus de génération.  
  
#### Pour substituer une cible prédéfinie  
  
1.  Identifiez dans Microsoft.Common.targets une cible prédéfinie que vous souhaitez substituer.  Consultez le tableau ci\-dessous pour obtenir la liste complète des cibles que vous pouvez substituer sans risque.  
  
2.  Définissez la cible ou les cibles à la fin de votre fichier projet, immédiatement avant la balise `</Project>`.  Par exemple :  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  Générez le fichier projet.  
  
 Le tableau suivant affiche toutes les cibles de Microsoft.Common.targets que vous pouvez substituer sans risque.  
  
|Nom de la cible|Description|  
|---------------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après que la compilation principale a eu lieu.  La plupart des personnalisations sont faites dans l'une de ces deux cibles.|  
|`BeforeBuild`, `AfterBuild`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après toutes les autres tâches de la génération. **Note:**  Les cibles `BeforeBuild` et `AfterBuild` sont déjà définies dans les commentaires à la fin de la plupart des fichiers projet.  Vous pouvez ainsi ajouter facilement des événements pre\-build et post\-build à votre fichier projet.|  
|`BeforeRebuild`, `AfterRebuild`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après l'appel de la fonctionnalité de régénération principale.  L'ordre de l'exécution cible dans Microsoft.Common.targets est le suivant : `BeforeRebuild`, `Clean`, `Build`, puis `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après l'appel de la fonctionnalité de nettoyage principale.|  
|`BeforePublish`, `AfterPublish`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après l'appel de la fonctionnalité d'édition principale.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après la résolution des références d'assembly.|  
|`BeforeResGen`, `AfterResGen`|Les tâches insérées dans l'une de ces cibles s'exécutent avant ou après la génération des ressources.|  
  
## Substitution des propriétés « DependsOn »  
 La substitution de cibles prédéfinies permet d'étendre facilement le processus de génération, mais, comme [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] évalue séquentiellement la définition des cibles, il est impossible d'empêcher un autre projet qui importe votre projet de substituer les cibles que vous avez déjà substituées.  Ainsi, par exemple, la dernière cible `AfterBuild` définie dans le fichier projet, après que tous les autres projets ont été importés, sera celle utilisée pendant la génération.  
  
 Vous pouvez vous préserver des substitutions involontaires de cibles en substituant les propriétés « DependsOn » utilisées dans les attributs `DependsOnTargets` à travers l'ensemble du fichier Microsoft.Common.targets.  Par exemple, la cible `Build` contient une valeur d'attribut `DependsOnTargets` égale à `"$(BuildDependsOn)"`.  Considérez :  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Ce code XML indique qu'avant que la cible `Build` ne puisse s'exécuter, toutes les cibles spécifiées dans la propriété `BuildDependsOn` doivent s'exécuter au préalable.  La propriété `BuildDependsOn` est définie comme suit :  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Vous pouvez substituer cette valeur de propriété en déclarant une autre propriété nommée `BuildDependsOn` à la fin de votre fichier projet.  En incluant la propriété `BuildDependsOn` précédente dans la nouvelle propriété, vous pouvez ajouter de nouvelles cibles au début et fin de la liste des cibles.  Par exemple :  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 Les projets qui importent vos fichiers projet peuvent substituer ces propriétés sans remplacer les personnalisations que vous avez faites.  
  
#### Pour substituer une propriété « DependsOn »  
  
1.  Identifiez une propriété « DependsOn » prédéfinie dans Microsoft.Common.targets que vous souhaitez substituer.  Voyez le tableau ci\-dessous pour obtenir la liste des propriétés « DependsOn » communément substituées.  
  
2.  Définissez une autre instance de la propriété ou des propriétés à la fin de votre fichier projet.  Incluez la propriété d'origine, par exemple `$(BuildDependsOn)`, dans la nouvelle propriété.  
  
3.  Définissez vos cibles personnalisées avant ou après la définition de propriété.  
  
4.  Générez le fichier projet.  
  
### Propriétés « DependsOn » communément substituées  
  
|Nom de la propriété|Description|  
|-------------------------|-----------------|  
|`BuildDependsOn`|Propriété à substituer si vous souhaitez insérer des cibles personnalisées avant ou après la totalité du processus de génération.|  
|`CleanDependsOn`|Propriété à substituer si vous souhaitez nettoyer la sortie de votre processus de génération personnalisée.|  
|`CompileDependsOn`|Propriété à substituer si vous souhaitez insérer des processus personnalisés avant ou après l'étape de compilation.|  
  
## Voir aussi  
 [Intégration Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [.Targets Files](../msbuild/msbuild-dot-targets-files.md)