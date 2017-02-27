---
title: "Comment&#160;: utiliser des caract&#232;res sp&#233;ciaux d&#39;&#233;chappement dans MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "séquence d’échappement des caractères spéciaux"
  - "caractères d’échappement"
  - "caractères d'échappement"
  - "MSBuild, échapper des caractères spéciaux"
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Comment : utiliser des caractères spéciaux d'échappement dans MSBuild
Certains caractères ont une signification spéciale dans les fichiers projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Il s’agit par exemple des points-virgules (;) et des astérisques (*). Pour obtenir la liste complète de ces caractères spéciaux, consultez l’article [Caractères spéciaux MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Pour utiliser ces caractères spéciaux en tant que littéraux dans un fichier projet, vous devez les spécifier à l’aide de la syntaxe %*xx*, où *xx* représente la valeur hexadécimale ASCII du caractère.  
  
## <a name="msbuild-special-characters"></a>Caractères spéciaux MSBuild  
 Par exemple, les caractères spéciaux sont utilisés dans l’attribut `Include` des listes d’éléments. Par exemple, la liste d’éléments suivante déclare deux éléments : `MyFile.cs` et `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Si vous souhaitez déclarer un élément qui contient un point-virgule dans le nom, vous devez utiliser la syntaxe %*xx* pour insérer le point-virgule dans une séquence d’échappement et empêcher [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de déclarer deux éléments distincts. Par exemple, l’élément suivant insère le point-virgule dans une séquence d’échappement et déclare un élément nommé `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Pour utiliser un caractère spécial MSBuild comme caractère littéral  
  
-   Utilisez la notation %*xx* à la place du caractère spécial, où *xx* représente la valeur hexadécimale du caractère ASCII. Par exemple, pour utiliser un astérisque (*) comme caractère littéral, utilisez la valeur `%2A`.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Éléments](../msbuild/msbuild.md)
 [MSBuild](../msbuild/msbuild-items.md)


<!--HONumber=Feb17_HO4-->


