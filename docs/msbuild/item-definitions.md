---
title: "Item Definitions | Microsoft Docs"
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
  - "msbuild, item definitions"
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Item Definitions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 permet la déclaration statique d'éléments dans les fichiers projet en utilisant l'élément [ItemGroup](../msbuild/itemgroup-element-msbuild.md).  Toutefois, les métadonnées peuvent uniquement être ajoutées au niveau de l'élément, même si les métadonnées sont identiques pour tous les éléments.  En commençant par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, un élément de projet nommé [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) passe outre cette limitation.  *ItemDefinitionGroup* vous permet de définir un jeu de définitions d'élément qui ajoutent des valeurs de métadonnées par défaut à tous les éléments du type nommé.  
  
 L'élément *ItemDefinitionGroup* apparaît immédiatement après l'élément [Project](../msbuild/project-element-msbuild.md) du fichier projet.  Les définitions d'élément offrent les fonctionnalités suivantes :  
  
-   Vous pouvez définir des métadonnées de configuration globales par défaut pour les éléments à l'extérieur d'une cible.  Autrement dit, les mêmes métadonnées s'appliquent à tous les éléments du type spécifié.  
  
-   Les types d'élément peuvent avoir plusieurs définitions.  Lorsque des caractéristiques de métadonnées supplémentaires sont ajoutées au type, la dernière spécification a la priorité. \(Les métadonnées suivent le même ordre d'importation que celui des propriétés.\)  
  
-   Les métadonnées peuvent être cumulatives.  Par exemple, les valeurs CDefines sont cumulées conditionnellement, selon les propriétés définies.  Par exemple, `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Les métadonnées peuvent être supprimées.  
  
-   Les conditions peuvent être utilisées pour contrôler l'inclusion de métadonnées.  
  
## Valeurs par défaut des métadonnées d'élément  
 Les métadonnées d'élément définies dans un ItemDefinitionGroup représentent juste une déclaration de métadonnées par défaut.  Les métadonnées ne s'appliquent pas à moins que vous ne définissiez un Item qui utilise un ItemGroup pour contenir les valeurs de métadonnées.  
  
> [!NOTE]
>  Dans beaucoup d'exemples de cette rubrique, un élément ItemDefinitionGroup est utilisé mais sa définition ItemGroup correspondante est omise pour des raisons de clarté.  
  
 Les métadonnées définies explicitement dans un ItemGroup on la priorité sur les métadonnées de ItemDefinitionGroup.  Les métadonnées d'ItemDefinitionGroup sont appliquées uniquement pour les métadonnées non définies dans un ItemGroup.  Par exemple :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 Dans cet exemple, la métadonnée par défaut "m" est appliquée à l'Élément "i" parce que la métadonnée "m" n'est pas explicitement définie par l'Élément "i".  Toutefois, la métadonnée par défaut "n" n'est pas appliquée à l'Élément "i" parce que la métadonnée "n" est déjà définie par l'Élément "i".  
  
> [!NOTE]
>  Les noms des éléments XML et des Paramètre respectent la casse.  Les métadonnées d'élément et les noms d'éléments\/propriétés ne respectent pas la casse.  Par conséquent, les éléments ItemDefinitionGroup possédant des noms qui diffèrent uniquement par la casse doivent être traités comme le même ItemGroup.  
  
## Sources de valeurs  
 Les valeurs pour les métadonnées définies dans un ItemDefinitionGroup peuvent provenir des nombreuses sources différentes suivantes :  
  
-   Propriété PropertyGroup  
  
-   Élément d'un ItemDefinitionGroup  
  
-   Transformation d'élément sur un élément ItemDefinitionGroup  
  
-   Variable d'environnement  
  
-   Propriété globale \(de la ligne de commande de MSBuild.exe\)  
  
-   Propriété réservée  
  
-   Métadonnées connues pour un élément d'un ItemDefinitionGroup  
  
-   La section CDATA \<\!\[CDATA \[toute donnée contenue ici n'est pas analysée\]\>  
  
> [!NOTE]
>  Les métadonnées d'élément d'un ItemGroup ne sont pas utiles dans une déclaration de métadonnées ItemDefinitionGroup car les éléments ItemDefinitionGroup sont traités avant les éléments ItemGroup.  
  
## Définitions additives et multiples  
 Lorsque vous ajoutez des définitions ou utilisez plusieurs ItemDefinitionGroups, ayez en tête ce qui suit.  
  
-   La spécification supplémentaire de métadonnées est ajoutée au type.  
  
-   La dernière spécification est prioritaire.  
  
 Lorsque vous avez plusieurs ItemDefinitionGroups, chaque spécification ultérieure ajoute ses métadonnées à la définition précédente.  Par exemple :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Dans cet exemple, la métadonnées "o" est ajoutée à "m" et "n".  
  
 De plus, les valeurs de métadonnées définies au préalable peuvent également être ajoutées.  Par exemple :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 Dans cet exemple, la valeur précédemment définie pour la métadonnée "m" \(m1\) est ajoutée à la nouvelle valeur \(m2\), afin que la valeur définitive soit "m1;m2".  
  
> [!NOTE]
>  Cela peut également se produire dans le même ItemDefinitionGroup.  
  
 Lorsque vous substituez les métadonnées définies précédemment, la dernière spécification a la priorité.  Dans l'exemple suivant, la dernière valeur de la métadonnée "m" passe de "m1" à "m1a".  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## Utilisation de conditions dans un ItemDefinitionGroup  
 Vous pouvez utiliser des conditions dans un ItemDefinitionGroup pour contrôler l'inclusion de métadonnées.  Par exemple :  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Dans ce cas, la métadonnée par défaut "m1" sur élément "i" est incluse uniquement si la valeur de la propriété "Configuration" est "Debug".  
  
> [!NOTE]
>  Seules les références de métadonnées locales sont prises en charge par les conditions.  
  
 Les références aux métadonnées définies dans un ItemDefinitionGroup antérieur sont locales à l'élément, pas au groupe de définition.  Autrement dit, la portée des références est spécifique à l'élément.  Par exemple :  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Dans cet exemple, l'élément "i" référence l'élément "test" dans la condition.  
  
## Substitution et suppression de métadonnées  
 Les métadonnées définies dans un élément ItemDefinitionGroup peuvent être substitués dans un élément ItemDefinitionGroup ultérieur attribuant une valeur vide aux métadonnées.  Vous pouvez également supprimer efficacement un élément de métadonnées en lui attribuant une valeur vide.  Par exemple :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 L'élément "i" contient encore les métadonnées "m", mais sa valeur est maintenant vide.  
  
## Portée des métadonnées  
 Les ItemDefinitionGroups ont une portée globale sur les propriétés définies et globales aux emplacements où elles sont définies.  Les définitions de métadonnées par défaut dans un ItemDefinitionGroup peuvent être auto\-référentielles.  L'exemple suivant utilise une référence de métadonnées simple :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Une référence de métadonnées qualifiée peut également être utilisée :  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Toutefois, les éléments suivants ne sont pas valides :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Depuis [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, les ItemGroups peuvent également être auto\-référentiels.  Par exemple :  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## Voir aussi  
 [Batching](../msbuild/msbuild-batching.md)