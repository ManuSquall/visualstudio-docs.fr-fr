---
title: "Task Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Task element [MSBuild]"
  - "<Task> element [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Task Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crée et exécute une instance d'une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Le nom d'élément est déterminé par le nom de la tâche créée.  
  
## Syntaxe  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Condition`|Attribut facultatif.  Condition à évaluer.  Pour plus d’informations, consultez [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Attribut facultatif.  Peut contenir une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**.  Lorsqu'une tâche échoue, les tâches suivantes dans l'élément de [cible](../msbuild/target-element-msbuild.md) et la génération continue à exécuter, et toutes les erreurs de la tâche sont traitées comme avertissements.<br />-   **ErrorAndContinue**.  Lorsqu'une tâche échoue, les tâches suivantes dans l'élément d' `Target` et la génération continue à exécuter, et toutes les erreurs de la tâche sont traitées comme des erreurs.<br />-   **ErrorAndStop** ou **false** \(valeur par défaut\).  Lorsqu'une tâche échoue, les tâches restantes dans l'élément d' `Target` et la génération ne sont pas exécutées, et l'élément entier d' `Target` et la génération est considéré comme ayant échoué.<br /><br /> Les versions du .NET Framework avant 4,5 pris en charge uniquement les valeurs d' `true` et d' `false` .<br /><br /> Pour plus d’informations, consultez [How to: Ignore Errors in Tasks](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md).|  
|`Parameter`|Obligatoire si la classe de la tâche contient une ou plusieurs propriétés dotées de l'attribut `[Required]`.<br /><br /> Paramètre de tâche défini par l'utilisateur qui contient la valeur du paramètre comme valeur.  L'élément `Task` peut avoir un nombre quelconque de paramètres, chaque attribut étant mappé à une propriété .NET dans la classe de la tâche.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Sortie](../msbuild/output-element-msbuild.md)|Stocke des sorties de la tâche dans le fichier projet.  Une tâche peut ne contenir aucun élément `Output` ou en contenir plusieurs.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Cible](../msbuild/target-element-msbuild.md)|Élément conteneur pour les tâches [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Notes  
 Un élément `Task` d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crée une instance de tâche, définit ses propriétés puis l'exécute.  L'élément `Output` stocke des paramètres de sortie dans des propriétés ou éléments afin de les utiliser ailleurs dans le fichier projet.  
  
 S'il existe des éléments [OnError](../msbuild/onerror-element-msbuild.md) dans l'élément `Target` parent d'une tâche, ils sont néanmoins évalués si la tâche échoue et que `ContinueOnError` a la valeur `false`.  Pour plus d'informations sur les tâches, consultez [Tasks](../msbuild/msbuild-tasks.md).  
  
## Exemple  
 L'exemple de code suivant crée une instance de la classe de la tâche [Csc](../msbuild/csc-task.md), définit six de ses propriétés et exécute la tâche.  Au terme de l'exécution, la valeur de la propriété `OutputAssembly` de l'objet est placée dans une liste d'éléments nommée `FinalAssemblyName`.  
  
```  
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
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)