---
title: Élément Task (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 123b3c0c66d162b62d8f925ab58679a95fc3838f
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326759"
---
# <a name="task-element-msbuild"></a>Task, élément (MSBuild)
Crée et exécute une instance d’une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Le nom de l’élément est déterminé par le nom de la tâche en cours de création.  

 \<Project>  
 \<Target>  

## <a name="syntax"></a>Syntaxe  

```xml  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Condition`|Attribut facultatif. Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Attribut facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, consultez [Guide pratique pour ignorer des erreurs dans des tâches](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Il est nécessaire si la classe de tâche contient une ou plusieurs propriétés dotées de l’attribut `[Required]`.<br /><br /> Un paramètre de tâche défini par l’utilisateur qui contient la valeur du paramètre comme sa propre valeur. Le nombre de paramètres dans l’élément `Task` peut varier, avec chaque attribut correspondant à une propriété .NET dans la classe de tâche.|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|[Sortie](../msbuild/output-element-msbuild.md)|Stocke des sorties de la tâche dans le fichier projet. Une tâche peut ne contenir aucun élément `Output` ou en contenir plusieurs.|  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Élément conteneur des tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Notes  
 Un élément `Task` dans un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crée une instance d’une tâche, définit des propriétés sur celle-ci et l’exécute. L’élément `Output` stocke les paramètres de sortie dans les propriétés ou les éléments à utiliser ailleurs dans le fichier projet.  

 S’il existe des éléments [OnError](../msbuild/onerror-element-msbuild.md) dans l’élément `Target` parent d’une tâche, ils seront néanmoins évalués si la tâche échoue, et `ContinueOnError` a la valeur de `false`. Pour plus d’informations sur les tâches, consultez [Tâches MSBuild](../msbuild/msbuild-tasks.md).  

## <a name="example"></a>Exemple  
 L’exemple de code suivant crée une instance de la classe [CSC, tâche](../msbuild/csc-task.md), définit six des propriétés et exécute la tâche. Après exécution, la valeur de la propriété `OutputAssembly` de l’objet est placée dans une liste d’éléments nommée `FinalAssemblyName`.  

```xml  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)
