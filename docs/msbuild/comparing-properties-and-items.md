---
title: "Comparaison des propri&#233;t&#233;s et des &#233;l&#233;ments | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, propriétés msbuild"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comparaison des propri&#233;t&#233;s et des &#233;l&#233;ments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Propriétés MSBuild et des éléments sont utilisés pour passer des informations aux tâches, évaluer des conditions et stocker des valeurs qui peuvent être référencés dans tout le fichier projet.  
  
-   Les propriétés sont des paires nom-valeur. Pour plus d’informations, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).  
  
-   Les éléments sont des objets qui représentent généralement des fichiers. Objets d’élément peuvent avoir des collections de métadonnées associées. Métadonnées sont des paires nom-valeur. Pour plus d’informations, consultez [éléments](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Scalaires et les vecteurs  
 Étant donné que les propriétés MSBuild sont des paires nom-valeur qui ont seulement une valeur de chaîne, ils sont souvent décrits comme *scalaire*. Étant donné que les types d’éléments MSBuild sont des listes d’éléments, ils sont souvent décrits comme *vecteur*. Toutefois, en pratique, les propriétés peuvent représenter plusieurs valeurs et des types d’éléments peuvent avoir zéro ou un élément.  
  
### <a name="target-dependency-injection"></a>Injection de dépendance cible  
 Pour voir comment les propriétés peuvent représenter plusieurs valeurs, envisagez un modèle d’utilisation commun pour l’ajout d’une cible à la liste des cibles à générer. Cette liste est généralement représentée par une valeur de propriété, avec les noms de cibles séparés par des points-virgules.  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Le `BuildDependsOn` propriété est généralement utilisée comme argument d’une cible `DependsOnTargets` attribut, le convertit efficacement en une liste d’éléments. Cette propriété peut être substituée pour ajouter une cible ou pour modifier l’ordre d’exécution des cibles. Par exemple :  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Ajoute la cible CustomBuild à la liste cible, ce qui donne `BuildDependsOn` la valeur `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 À compter de MSBuild 4.0, l’injection de dépendance cible est déconseillée. Utilisez le `AfterTargets` et `BeforeTargets` à la place des attributs. Pour plus d’informations, consultez [ordre de la génération cible](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Conversions entre des chaînes et des listes d’éléments  
 MSBuild effectue les conversions vers et depuis des types d’éléments et les valeurs de chaîne en fonction des besoins. Pour voir comment une liste d’éléments peut devenir une valeur de chaîne, considérez ce qui arrive lorsqu’un type d’élément est utilisé comme la valeur d’une propriété MSBuild :  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Le type d’élément OutputDir a un `Include` attribut avec la valeur « KeyFiles\\; Certificats\\». MSBuild analyse cette chaîne en deux éléments : KeyFiles\ et certificats\\. Lorsque le type d’élément OutputDir est utilisé comme valeur de la propriété OutputDirList, MSBuild convertit ou « aplanit » le type d’élément dans la chaîne délimitée par des points-virgules « KeyFiles\\; Certificats\\».  
  
## <a name="properties-and-items-in-tasks"></a>Propriétés et éléments de tâches  
 Propriétés et les éléments sont utilisés comme entrées et sorties des tâches MSBuild. Pour plus d’informations, consultez [tâches](../msbuild/msbuild-tasks.md).  
  
 Propriétés sont passées aux tâches en tant qu’attributs. Dans la tâche, une propriété MSBuild est représentée par un type de propriété dont la valeur peut être convertie vers et à partir d’une chaîne. Les types de propriété pris en charge incluent `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, et tout autre type dont <xref:System.Convert.ChangeType%2A> peut gérer.  
  
 Les éléments sont transmis aux tâches en tant que <xref:Microsoft.Build.Framework.ITaskItem> objets. Dans la tâche, <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> représente la valeur de l’élément et <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> récupère ses métadonnées.  
  
 La liste d’éléments d’un type d’élément peut être passée comme un tableau de `ITaskItem` objets. À compter de .NET Framework 3.5, éléments peuvent être supprimés à partir d’une liste d’éléments dans une cible à l’aide de la `Remove` attribut. Étant donné que les éléments peuvent être supprimés à partir d’une liste d’éléments, il est possible pour un type d’élément ait zéro élément. Si une liste d’éléments est passée à une tâche, le code de la tâche doit vérifier cette possibilité.  
  
## <a name="property-and-item-evaluation-order"></a>Propriété et l’ordre des éléments d’évaluation  
 Pendant la phase d’évaluation d’une build, les fichiers importés sont incorporés à la build dans l’ordre dans lequel ils apparaissent. Propriétés et des éléments sont définis en trois phases dans l’ordre suivant :  
  
-   Propriétés sont définies et modifiées dans l’ordre dans lequel ils apparaissent.  
  
-   Définitions d’élément sont définies et modifiées dans l’ordre dans lequel ils apparaissent.  
  
-   Les éléments sont définis et modifiés dans l’ordre dans lequel ils apparaissent.  
  
 Pendant la phase d’exécution d’une build, les propriétés et les éléments qui sont définis dans des cibles sont évaluées ensemble en une seule phase dans l’ordre dans lequel ils apparaissent.  
  
 Toutefois, cela n’est pas complet. Lorsqu’une propriété, une définition d’élément ou un élément est définie, sa valeur est évaluée. L’évaluateur d’expression développe la chaîne qui spécifie la valeur. L’expansion de chaîne dépend de la phase de génération. Voici un ordre d’évaluation éléments et de propriétés plus détaillé :  
  
-   Pendant la phase d’évaluation d’une build :  
  
    -   Propriétés sont définies et modifiées dans l’ordre dans lequel ils apparaissent. Fonctions de propriété sont exécutées. Les valeurs de propriété dans le $ (NomPropriété) formulaire sont développées dans des expressions. La valeur de propriété est définie à l’expression développée.  
  
    -   Définitions d’élément sont définies et modifiées dans l’ordre dans lequel ils apparaissent. Fonctions de propriétés ont déjà été développées dans des expressions. Les valeurs de métadonnées sont définies pour les expressions développées.  
  
    -   Types d’éléments sont définis et modifiés dans l’ordre dans lequel ils apparaissent. Élément valeurs sous la forme @(ItemType) sont développées. Transformations d’élément sont également développées. Les valeurs et les fonctions de propriétés ont déjà été développées dans des expressions. Les valeurs de liste et les métadonnées d’élément sont définies pour les expressions développées.  
  
-   Pendant la phase d’exécution d’une build :  
  
    -   Propriétés et des éléments qui sont définis dans des cibles sont évalués ensemble dans l’ordre dans lequel ils apparaissent. Fonctions de propriété sont exécutées et les valeurs de propriété sont développées dans des expressions. Valeurs d’élément et les transformations d’élément sont également développées. Les valeurs de propriété, les valeurs de type élément et des valeurs de métadonnées sont définies pour les expressions développées.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Effets discrets de l’ordre d’évaluation  
 Dans la phase d’évaluation d’une build, l’évaluation des propriétés précède évaluation de l’élément. Néanmoins, les propriétés peuvent avoir des valeurs qui s’affichent dépendent des valeurs d’élément. Examinez le script suivant.  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 L’exécution de la tâche Message affiche ce message :  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 C’est parce que la valeur de `KeyFileVersion` correspond à la chaîne "@(KeyFile->'%(Version)')". élément et les transformations d’élément n'ont pas été développées lorsque la propriété a été définie, donc le `KeyFileVersion` propriété a été affectée à la valeur de la chaîne non développée.  
  
 Pendant la phase d’exécution de la build, lorsqu’il traite la tâche Message, MSBuild développe la chaîne "@(KeyFile->'%(Version)')" pour générer « 1.0.0.3 ».  
  
 Notez que le même message s’affiche même si les groupes de propriétés et d’éléments ont été annulées dans l’ordre.  
  
 Autre exemple, prenez en compte ce qui peut se produire lorsque les groupes de propriétés et d’éléments se trouvent dans des cibles :  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 La tâche Message affiche ce message :  
  
```  
KeyFileVersion:   
```  
  
 Effet, pendant la phase d’exécution de la build, les groupes de propriétés et d’éléments définis dans des cibles sont évalués de haut en bas en même temps. Lorsque `KeyFileVersion` est défini, `KeyFile` est inconnu. Par conséquent, la transformation d’élément se développe en une chaîne vide.  
  
 Dans ce cas, l’inversion de l’ordre des groupes de propriétés et d’éléments restaure le message d’origine :  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 La valeur de `KeyFileVersion` est définie sur « 1.0.0.3 » et non à "@(KeyFile->'%(Version)')". tâche le Message affiche ce message :  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)