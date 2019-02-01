---
title: Item, élément (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b45d0e9494700d03c0e96ccd0708e2754b4f7a2b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797023"
---
# <a name="item-element-msbuild"></a>Item, élément (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contient un élément défini par l'utilisateur et ses métadonnées. Chaque élément utilisé dans un projet [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] doit être spécifié en tant qu'enfant d'un élément `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Include`|Attribut requis.<br /><br /> Fichier ou caractère générique à inclure dans la liste des éléments.|  
|`Exclude`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à exclure de la liste des éléments.|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  
|`Remove`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à supprimer de la liste des éléments.<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
|`KeepMetadata`|Attribut facultatif.<br /><br /> Métadonnées des éléments sources à ajouter aux éléments cibles. Seules les métadonnées dont les noms sont spécifiés dans la liste délimitée par des points-virgules sont transférées depuis un élément source vers un élément cible. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
|`RemoveMetadata`|Attribut facultatif.<br /><br /> Métadonnées des éléments sources à ne pas transférer aux éléments cibles. Toutes les métadonnées sont transférées depuis un élément source vers un élément cible, à l'exception des métadonnées dont le nom figure dans la liste de noms délimitée par des points-virgules. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
|`KeepDuplicates`|Attribut facultatif.<br /><br /> Spécifie si un élément doit être ajouté au groupe cible s'il s'agit d'une copie exacte d'un élément existant. Si les éléments source et cible ont les mêmes valeurs `Include` mais des métadonnées différentes, l'élément est ajouté même si `KeepDuplicates` est défini sur `false`. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Clé de métadonnées d'élément définie par l'utilisateur, qui contient la valeur des métadonnées de l'élément. Un élément peut ne contenir aucun élément `ItemMetadata` ou en contenir plusieurs.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Élément grouping pour d’autres éléments.|  
  
## <a name="remarks"></a>Notes  
 Les éléments `Item` définissent les entrées du système de génération et sont regroupés en collections d'éléments, selon leur nom de collection défini par l'utilisateur. Ces collections d’éléments peuvent être utilisées comme paramètres des [tâches](../msbuild/msbuild-tasks.md), lesquelles utilisent les éléments d’une collection pour exécuter les étapes du processus de génération. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
 La notation `@(`*monType*`)` permet de développer une collection d’éléments de type *monType* en une liste de chaînes séparées par des points-virgules, et de la transmettre à un paramètre. Si le paramètre est de type `string`, la valeur du paramètre correspond à la liste des éléments séparés par des points-virgules. Si le paramètre est un tableau de chaînes (`string[]`), chaque élément est inséré dans le tableau selon l'emplacement des points-virgules. Si le paramètre de tâche est de type <xref:Microsoft.Build.Framework.ITaskItem>`[]`, la valeur correspond au contenu de la collection d'éléments et à toutes les métadonnées associées. Pour délimiter chaque élément à l’aide d’un caractère autre que le point-virgule, utilisez la syntaxe `@(`*monType*`, '`*séparateur*`')`.  
  
 Le moteur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] peut évaluer les caractères génériques tels que `*` et `?`, ainsi que les caractères génériques récursifs comme `/**/*.cs`. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment déclarer deux éléments de type `CSFile`. Le second élément déclaré contient les métadonnées dans lesquelles `MyMetadata` a la valeur `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments](../msbuild/msbuild-items.md)   
 [Propriétés MSBuild](msbuild-properties1.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
