---
title: Définitions d’éléments | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35506967ee20ff6c936e2de4a19d7860e154e4c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866569"
---
# <a name="item-definitions"></a>Définitions d'éléments
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 permet la déclaration statique d’éléments dans les fichiers projet à l’aide de l’élément [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Les métadonnées ne peuvent cependant être ajoutées qu’au niveau de l’élément, même si elles sont identiques pour tous les éléments. À compter de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, un élément de projet nommé [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) passe outre cette limitation. *ItemDefinitionGroup* vous permet de définir un ensemble de définitions d’élément, qui ajoutent des valeurs de métadonnées par défaut à tous les éléments dans le type d’élément nommé.  
  
 L’élément *ItemDefinitionGroup* apparaît immédiatement après l’élément [Project](../msbuild/project-element-msbuild.md) du fichier projet. Les définitions d’élément offrent les fonctionnalités suivantes :  
  
-   Vous pouvez définir des métadonnées par défaut globales pour les éléments en dehors d’une cible. Autrement dit, les mêmes métadonnées s’appliquent à tous les éléments du type spécifié.  
  
-   Les types d’éléments peuvent avoir plusieurs définitions. Quand des spécifications de métadonnées supplémentaires sont ajoutées au type, la dernière spécification est prioritaire. \(Les métadonnées suivent le même ordre d’importation que celui des propriétés.\)  
  
-   Les métadonnées peuvent être additionnées. Par exemple, les valeurs CDefines sont cumulées conditionnellement, en fonction des propriétés qui sont définies. Par exemple, `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Les métadonnées peuvent être supprimées.  
  
-   Des conditions peuvent être utilisées pour contrôler l’inclusion de métadonnées.  
  
## <a name="item-metadata-default-values"></a>Valeurs par défaut des métadonnées d’éléments  
 Les métadonnées d’éléments qui sont définies dans un ItemDefinitionGroup sont simplement une déclaration de métadonnées par défaut. Les métadonnées ne s’applique pas sauf si vous définissez un élément qui utilise un ItemGroup pour contenir les valeurs des métadonnées.  
  
> [!NOTE]
>  Dans la plupart des exemples de cette rubrique, un élément ItemDefinitionGroup est montré mais sa définition ItemGroup correspondante est omise par souci de clarté.  
  
 Les métadonnées explicitement définies dans un ItemGroup sont prioritaires sur les métadonnées dans ItemDefinitionGroup. Les métadonnées dans ItemDefinitionGroup sont appliquées uniquement pour les métadonnées non définies dans un ItemGroup. Exemple :  
  
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
  
 Dans cet exemple, les métadonnées par défaut « m » sont appliquées à l’élément « i », car les métadonnées « m » ne sont pas explicitement définies par l’élément « i ». Cependant, les métadonnées par défaut « n » ne sont pas appliquées à l’élément « i », car les métadonnées « n » sont déjà définies par l’élément « i ».  
  
> [!NOTE]
>  Les noms de paramètre et d’élément XML respectent la casse. Les noms des métadonnées d’élément et des éléments\/propriétés ne respectent pas la casse. Par conséquent, les éléments ItemDefinitionGroup ayant des noms qui diffèrent uniquement par la casse doivent être traités comme le même ItemGroup.  
  
## <a name="value-sources"></a>Sources des valeurs  
 Les valeurs pour les métadonnées définies dans un ItemDefinitionGroup peuvent provenir de nombreuses sources différentes, comme suit :  
  
-   Propriété PropertyGroup  
  
-   Élément d’un ItemDefinitionGroup  
  
-   Transformation d’élément sur un élément ItemDefinitionGroup  
  
-   Variable d’environnement  
  
-   Propriété globale \(de la ligne de commande MSBuild.exe\)  
  
-   Propriété réservée  
  
-   Métadonnées bien connues sur un élément d’un ItemDefinitionGroup  
  
-   Section CDATA \< \! \[CDATA\[rien ici n’est pas analysé\]\]\>  
  
> [!NOTE]
>  Les métadonnées d’élément d’un ItemGroup ne sont pas utiles dans une déclaration de métadonnées ItemDefinitionGroup, car les éléments ItemDefinitionGroup sont traités avant les éléments ItemGroup.  
  
## <a name="additive-and-multiple-definitions"></a>Définitions additives et multiples  
 Quand vous ajoutez des définitions ou que vous utilisez plusieurs ItemDefinitionGroup, gardez à l’esprit que :  
  
- Une spécification de métadonnées supplémentaires est ajoutée au type.  
  
- La dernière spécification est prioritaire.  
  
  Quand vous avez plusieurs ItemDefinitionGroup, chaque spécification ultérieure ajoute ses métadonnées à la définition précédente. Exemple :  
  
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
  
 Dans cet exemple, les métadonnées « o » sont ajoutées à « m » et à « n ».  
  
 En outre, les valeurs des métadonnées définies précédemment peuvent également être ajoutées. Exemple :  
  
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
  
 Dans cet exemple, la valeur précédemment définie pour les métadonnées « m » \(m1\) est ajoutée à la nouvelle valeur \(m2\), de sorte que la valeur finale est « m1;m2 ».  
  
> [!NOTE]
>  Ceci peut également se produire dans le même ItemDefinitionGroup.  
  
 Quand vous remplacez les métadonnées définies précédemment, la dernière spécification est prioritaire. Dans l’exemple suivant, la valeur finale des métadonnées « m » passe de « m1 » « m1a ».  
  
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
  
## <a name="using-conditions-in-an-itemdefinitiongroup"></a>Utilisation de conditions dans un ItemDefinitionGroup  
 Vous pouvez utiliser des conditions dans un ItemDefinitionGroup pour contrôler l’inclusion des métadonnées. Exemple :  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Dans ce cas, les métadonnées par défaut « m1 » sur l’élément « i » sont incluses seulement si la valeur de la propriété « Configuration » est « Debug ».  
  
> [!NOTE]
>  Seules les références de métadonnées locales sont prises en charge dans les conditions.  
  
 Les références aux métadonnées définies dans un ItemDefinitionGroup antérieur sont locales à l’élément, et non pas au groupe de définitions. Autrement dit, l’étendue des références sont spécifiques aux éléments. Exemple :  
  
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
  
 Dans cet exemple, élément « i » fait référence à élément « test » dans la Condition.  
  
## <a name="overriding-and-deleting-metadata"></a>Remplacement et suppression de métadonnées  
 Vous pouvez remplacer les métadonnées définies dans un élément ItemDefinitionGroup dans un élément ItemDefinitionGroup ultérieur en attribuant une valeur vide aux métadonnées. Vous pouvez aussi supprimer un élément de métadonnées en lui attribuant une valeur vide. Exemple :  
  
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
  
 L’élément « i » contient encore les métadonnées « m », mais sa valeur est maintenant vide.  
  
## <a name="scope-of-metadata"></a>Étendue des métadonnées  
 Les ItemDefinitionGroup ont une étendue globale sur les propriétés définies et globales là où elles sont définies. Les définitions de métadonnées par défaut dans un ItemDefinitionGroup peuvent se référencer elles-mêmes. Par exemple, ce qui suit utilise une référence de métadonnées simple :  
  
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
  
 L’exemple suivant n’est cependant pas valide :  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 À compter de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, les ItemGroup peuvent également se référencer eux-mêmes. Exemple :  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement par lots](../msbuild/msbuild-batching.md)



