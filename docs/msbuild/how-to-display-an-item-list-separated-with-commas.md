---
title: "Guide pratique pour afficher une liste d’éléments séparés par des virgules | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
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
ms.translationtype: HT
ms.sourcegitcommit: 38c6099f912424d21df2aeea4cfdd0401ba57465
ms.openlocfilehash: 9366ae0f599f7ae37de40fb1ae556c04f6e73292
ms.contentlocale: fr-fr
ms.lasthandoff: 07/14/2017

---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Comment : afficher une liste d'éléments séparés par des virgules
Lorsque vous utilisez des listes d’éléments dans [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), il est parfois utile d’afficher le contenu de ces listes de manière à faciliter leur lecture. Vous pouvez également avoir une tâche qui accepte une liste d’éléments séparés par une chaîne de séparation particulière. Dans ces deux cas, vous pouvez spécifier une chaîne de séparation pour la liste d’éléments.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Séparation des éléments d’une liste à l’aide de virgules  
 Par défaut, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utilise des points-virgules pour séparer les éléments d’une liste. Par exemple, imaginez un élément `Message` avec la valeur suivante :  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Lorsque la liste d’éléments `@(TXTFile)` contient les éléments App1.txt, App2.txt et App3.txt, le message est le suivant :  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Si vous souhaitez modifier le comportement par défaut, vous pouvez spécifier votre propre séparateur. La syntaxe à utiliser pour spécifier un séparateur d’éléments de liste est la suivante :  
  
 `@(ItemListName, '<separator>')`  
  
 Le séparateur peut être un caractère unique ou une chaîne, et doit être compris entre guillemets simples.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Pour insérer une virgule et un espace entre les éléments  
  
-   Utilisez une notation d’éléments semblable à celle-ci :  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la tâche [Exec](../msbuild/exec-task.md) exécute l’outil findstr pour rechercher des chaînes de texte spécifiées dans le fichier Phrases.txt. Dans la commande findstr, les chaînes de recherche littérales sont indiquées par le commutateur **/c:**. Ainsi, le séparateur d’éléments `/c:` est inséré entre les éléments de la liste `@(Phrase)`.  
  
 Pour cet exemple, la commande équivalente de ligne de commande est la suivante :  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```xml  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Éléments MSBuild](../msbuild/msbuild-items.md)
