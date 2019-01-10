---
title: Métadonnées d’éléments dans le traitement par lots de tâches | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38f8691cc7b1b102b0d1747d8bd9a94411608f22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891412"
---
# <a name="item-metadata-in-task-batching"></a>Métadonnées d’élément dans le traitement par lots des tâches
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] a la capacité de diviser les listes d’éléments en différentes catégories, ou lots, en fonction des métadonnées des éléments, et d’exécuter une tâche une fois avec chaque lot. Il peut être difficile de comprendre exactement quels éléments sont passés avec quel lot. Cette rubrique couvre les scénarios courants suivants qui impliquent un traitement par lots.  
  
-   Division d’une liste d’éléments en lots  
  
-   Division de plusieurs listes d’éléments en lots  
  
-   Traitement par lots d’un élément à la fois  
  
-   Filtrage de listes d’éléments  

Pour plus d’informations sur le traitement par lots avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consultez [Traitement par lots](../msbuild/msbuild-batching.md).  
  
## <a name="divide-an-item-list-into-batches"></a>Diviser une liste d’éléments en lots  
 Le traitement par lots vous permet de diviser une liste d’éléments en différents lots en fonction des métadonnées des éléments et de passer chacun des lots séparément dans une tâche. Ceci est utile pour générer des assemblys satellites.  
  
 L’exemple suivant montre comment diviser une liste d’éléments en lots en fonction des métadonnées des éléments. La liste d’éléments `ExampColl` est divisée en trois lots en fonction des métadonnées de l’élément `Number`. La présence de `%(ExampColl.Number)` dans l’attribut `Text` indique à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qu’un traitement par lots doit être effectué. La liste d’éléments `ExampColl` est divisée en trois lots en fonction des métadonnées `Number` et chaque lot est passé séparément dans la tâche.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  

La [tâche Message](../msbuild/message-task.md) affiche les informations suivantes :  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="divide-several-item-lists-into-batches"></a>Diviser plusieurs listes d’éléments en lots  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut diviser plusieurs listes d’éléments en lots en fonction des métadonnées identiques. Ceci facilite la division de différentes listes d’éléments en lots pour générer plusieurs assemblys. Par exemple, vous pouvez avoir une liste d’éléments de fichiers *.cs* divisée en un lot d’application et un lot d’assembly, et une liste d’éléments de fichiers de ressources divisée en un lot d’application et un lot d’assembly. Vous pouvez ensuite utiliser le traitement par lots pour passer ces listes d’éléments dans une même tâche et générer l’application et l’assembly.  
  
> [!NOTE]
>  Si une liste d’éléments passée dans une tâche ne contient aucun élément avec les métadonnées référencées, chaque élément de cette liste est passé dans chaque lot.  
  
L’exemple suivant montre comment diviser une liste de plusieurs éléments en lots en fonction des métadonnées des éléments. Les listes d’éléments `ExampColl` et `ExampColl2` sont divisées en trois lots en fonction des métadonnées de l’élément `Number`. La présence de `%(Number)` dans l’attribut `Text` indique à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qu’un traitement par lots doit être effectué. Les listes d’éléments `ExampColl` et `ExampColl2` sont divisées en trois lots en fonction des métadonnées `Number` et chaque lot est passé séparément dans la tâche.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
La [tâche Message](../msbuild/message-task.md) affiche les informations suivantes :  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batch-one-item-at-a-time"></a>Traiter par lots un élément à la fois  
 Le traitement par lots peut également être effectué sur les métadonnées d’éléments connus qui sont affectés à chaque élément à la création. Cela garantit que chaque élément d’une collection a des métadonnées à utiliser pour le traitement par lots. La valeur des métadonnées `Identity` est unique pour chaque élément et est utile pour diviser chaque élément d’une liste d’éléments en un lot distinct. Pour obtenir la liste complète des métadonnées d’élément connues, consultez [Métadonnées d’élément connues](../msbuild/msbuild-well-known-item-metadata.md).  
  
 L’exemple suivant montre comment traiter par lots chaque élément d’une liste d’éléments un à la fois. Comme la valeur des métadonnées `Identity` de chaque élément est unique, la liste d’éléments `ExampColl` est divisée en six lots, chacun contenant un élément de la liste d’éléments. La présence de `%(Identity)` dans l’attribut `Text` indique à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] qu’un traitement par lots doit être effectué.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
La [tâche Message](../msbuild/message-task.md) affiche les informations suivantes :  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filter-item-lists"></a>Filtrer des listes d’éléments  
 Le traitement par lots peut être utilisé pour filtrer certains éléments d’une liste d’éléments avant de la passer à une tâche. Par exemple, le filtrage sur les valeurs de métadonnées d’éléments connues `Extension` vous permet d’exécuter une tâche seulement sur des fichiers avec une extension spécifique.  
  
 L’exemple suivant montre comment diviser une liste d’éléments en lots en fonction des métadonnées des éléments, puis filtrer ces lots quand ils sont passés dans une tâche. La liste d’éléments `ExampColl` est divisée en trois lots en fonction des métadonnées de l’élément `Number`. L’attribut `Condition` de la tâche spécifie que seuls les lots avec une valeur de métadonnées d’élément `Number` égale à `2` doivent être passés dans la tâche.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
La [tâche Message](../msbuild/message-task.md) affiche les informations suivantes :  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Métadonnées d’élément connues](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item, élément (MSBuild)](../msbuild/item-element-msbuild.md)   
 [ItemMetadata, élément (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Traitement par lot MSBuild](../msbuild/msbuild-batching.md)   
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
