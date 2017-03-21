---
title: "Élément Item (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 927d80ec00ee69ca6aa59f257826307bcd3fe513
ms.lasthandoff: 03/01/2017

---
# <a name="item-element-msbuild"></a>Item, élément (MSBuild)
Contient un élément défini par l'utilisateur et ses métadonnées. Chaque élément utilisé dans un projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit être spécifié en tant qu'enfant d'un élément `ItemGroup`.  

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

## <a name="specify-metadata-as-attributes"></a>Spécifier de métadonnées en tant qu’attributs
Dans MSBuild version 15.1 ou ultérieure, toutes les métadonnées dont le nom n’entre pas en conflit avec la liste actuelle des attributs peuvent éventuellement être exprimées en tant qu’attribut.

Par exemple, pour spécifier une liste de packages NuGet, vous utiliseriez normalement une syntaxe similaire à la suivante.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

À présent, toutefois, vous pouvez passer les métadonnées `Version` en tant qu’attribut, comme dans la syntaxe suivante :

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Include`|Attribut requis.<br /><br /> Fichier ou caractère générique à inclure dans la liste des éléments.|  
|`Exclude`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à exclure de la liste des éléments.|  
|`Condition`|Attribut facultatif.<br /><br /> Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  
|`Remove`|Attribut facultatif.<br /><br /> Fichier ou caractère générique à supprimer de la liste des éléments.<br /><br />|  
|`KeepDuplicates`|Attribut facultatif.<br /><br /> Spécifie si un élément doit être ajouté au groupe cible s'il s'agit d'une copie exacte d'un élément existant. Si les éléments source et cible ont les mêmes valeurs `Include` mais des métadonnées différentes, l'élément est ajouté même si `KeepDuplicates` est défini sur `false`. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
|`KeepMetadata`|Attribut facultatif.<br /><br /> Métadonnées des éléments sources à ajouter aux éléments cibles. Seules les métadonnées dont les noms sont spécifiés dans la liste délimitée par des points-virgules sont transférées depuis un élément source vers un élément cible. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
|`RemoveMetadata`|Attribut facultatif.<br /><br /> Métadonnées des éléments sources à ne pas transférer aux éléments cibles. Toutes les métadonnées sont transférées depuis un élément source vers un élément cible, à l'exception des métadonnées dont le nom figure dans la liste de noms délimitée par des points-virgules. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).<br /><br /> Cet attribut n'est valide que s'il est spécifié pour un élément d'un `ItemGroup` présent dans un `Target`.|  
|`Update`|Attribut facultatif. (Disponible uniquement pour les projets .NET Core dans Visual Studio versions 2017 ou ultérieures).<br /><br /> Vous permet de modifier les métadonnées d’un fichier qui a été inclus à l’aide d’un glob.<br /><br />  Cet attribut n’est valide que s’il est spécifié pour un élément d’un `ItemGroup` qui n’est pas présent dans un `Target`.|  

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

 La notation `@(`*monType*`)` permet de développer une collection d’éléments de type *monType* en une liste de chaînes séparées par des points-virgules, et de la transmettre à un paramètre. Si le paramètre est de type `string`, la valeur du paramètre correspond à la liste des éléments séparés par des points-virgules. Si le paramètre est un tableau de chaînes (`string[]`), chaque élément est inséré dans le tableau selon l'emplacement des points-virgules. Si le paramètre de tâche est de type <xref:Microsoft.Build.Framework.ITaskItem>`[]`, la valeur correspond au contenu de la collection d’éléments et à toutes les métadonnées associées. Pour délimiter chaque élément à l’aide d’un caractère autre que le point-virgule, utilisez la syntaxe `@(`*monType*`, '`*séparateur*`')`.  

 Le moteur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] peut évaluer les caractères génériques tels que `*` et `?`, ainsi que les caractères génériques récursifs comme `/**/*.cs`. Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Exemples  
 L'exemple de code suivant montre comment déclarer deux éléments de type `CSFile`. Le second élément déclaré contient les métadonnées dans lesquelles `MyMetadata` a la valeur `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
L’exemple de code suivant montre comment utiliser l’attribut `Update` pour modifier les métadonnées dans un fichier appelé somefile.cs fourni par le biais d’un glob. (Disponible uniquement pour les projets .NET Core dans Visual Studio versions 2017 ou ultérieures).

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Voir aussi  
 [Éléments](../msbuild/msbuild-items.md)   
 [Propriétés MSBuild](../msbuild/msbuild-properties.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)

