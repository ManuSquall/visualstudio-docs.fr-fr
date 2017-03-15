---
title: "Item Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, Item functions"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Item Functions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

À compter de MSBuild 4.0, le code des tâches et des cibles peut appeler des fonctions d'élément pour obtenir des informations sur les éléments dans le projet.  Ces fonctions simplifient l'obtention des éléments Distinct\(\) et sont plus rapides que l'exécution d'une boucle sur les éléments.  
  
## Fonctions d'élément de chaîne  
 Vous pouvez utiliser les méthodes et les propriétés de chaîne dans le.NET Framework pour traiter une valeur d'élément.  Pour les méthodes d' <xref:System.String> , spécifiez le nom de la méthode.  Pour les propriétés d' <xref:System.String> , spécifiez le nom de la propriété après « get\_ ».  
  
 Pour les éléments qui ont plusieurs chaînes, la méthode de chaîne ou des séries de propriété sur chaque chaîne.  
  
 l'exemple suivant montre comment utiliser ces fonctions d'élément de chaîne.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## Fonctions intrinsèques d'élément  
 Le tableau ci\-dessous répertorie les fonctions intrinsèques disponibles pour les éléments.  
  
|Fonction|Exemple|Description|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Retourne le nombre d'éléments.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Retourne l'équivalent d' `Path.DirectoryName` pour chaque élément.|  
|`Distinct`|`@(MyItem->Distinct())`|Retourne les éléments qui ont des valeurs distinctes d' `Include` .  Les métadonnées sont ignorées.  La comparaison ne respecte pas la casse.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Retourne les éléments qui ont des valeurs distinctes d' `itemspec` .  Les métadonnées sont ignorées.  La comparaison respecte la casse.|  
|`Reverse`|`@(MyItem->Reverse())`|Retourne les éléments dans l'ordre inverse.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Retourne `boolean` pour indiquer si un élément est le nom de métadonnées et la valeur donnés.  La comparaison ne respecte pas la casse.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Retourne des éléments avec leurs métadonnées effacées.  Uniquement `itemspec` est conservé.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Retourne les éléments qui ont le nom des métadonnées donné.  La comparaison ne respecte pas la casse.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Retourne la valeur des métadonnées portant le nom des métadonnées.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Retourne les éléments qui ont le nom des métadonnées et la valeur donnés.  La comparaison ne respecte pas la casse.|  
  
 l'exemple suivant montre comment utiliser des fonctions intrinsèques d'élément.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## Voir aussi  
 [Items](../msbuild/msbuild-items.md)