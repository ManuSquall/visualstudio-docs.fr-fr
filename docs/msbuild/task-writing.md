---
title: "Task Writing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, writing tasks"
  - "tasks, creating for MSBuild"
  - "MSBuild, creating tasks"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Task Writing
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les tâches fournissent le code exécuté pendant le processus de génération.  Les tâches sont contenues dans les cibles.  Une bibliothèque de tâches courantes est fournie avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], et vous pouvez également écrire vos propres tâches.  Pour plus d'informations sur la bibliothèque des tâches incluses dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consultez [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## Tâches  
 Les exemples de tâches comprennent [Copy](../msbuild/copy-task.md), qui copie un ou plusieurs fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée un répertoire, et [Csc](../msbuild/csc-task.md), qui compile des fichiers de code source [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Chaque tâche est implémentée comme une classe .NET qui implémente l'interface <xref:Microsoft.Build.Framework.ITask>, qui est définie dans l'assembly Microsoft.Build.Framework.dll.  
  
 Vous pouvez suivre deux approches pour implémenter une tâche :  
  
-   Implémentez l'interface <xref:Microsoft.Build.Framework.ITask> directement.  
  
-   Dérivez votre classe de la classe d'assistance, <xref:Microsoft.Build.Utilities.Task>, qui est définie dans l'assembly Microsoft.Build.Utilities.dll.  La tâche implémente ITask et fournit des implémentations par défaut de quelques membres ITask.  En outre, la journalisation est plus facile.  
  
 Dans les deux cas, vous devez ajouter à votre classe une méthode nommée `Execute`, qui est la méthode qui est appelée lorsque la tâche s'exécute.  Cette méthode ne prend pas de paramètres et retourne une valeur `Boolean` : `true` si la tâche a réussi ou `false` si elle a échoué.  L'exemple suivant montre une tâche que n'exécute aucune action et retourne `true`.  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Le fichier projet suivant exécute cette tâche :  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Lorsque les tâches sont exécutées, elles peuvent également recevoir des entrées du fichier projet si vous créez des propriétés .NET sur la classe de tâche.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] définit ces propriétés immédiatement avant d'appeler la méthode `Execute` de la tâche.  Pour créer une propriété de type chaîne, utilisez un code de tâche tel que :  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Le fichier projet suivant exécute cette tâche et affecte la valeur donnée à `MyProperty` :  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## Inscription de tâches  
 Si un projet va exécuter une tâche, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] doit savoir comment localiser l'assembly qui contient la classe de tâche.  Les tâches sont inscrites à l'aide de l'[UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
 Le fichier Microsoft.Common.Tasks [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est un fichier projet qui contient une liste d'éléments `UsingTask` qui inscrivent toutes les tâches qui sont fournies avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Ce fichier est automatiquement inclus à chaque génération de projet.  Si une tâche qui est inscrite dans Microsoft.Common.Tasks est également inscrite dans le fichier projet actuel, le fichier projet actuel a la priorité, ce qui signifie que vous pouvez substituer une tâche par défaut par votre propre tâche du même nom.  
  
> [!TIP]
>  Vous pouvez consulter une liste de tâches qui sont fournies avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en affichant le contenu de Microsoft.Common.Tasks.  
  
## Déclenchement d'événements à partir d'une tâche  
 Si votre tâche dérive de la classe d'assistance <xref:Microsoft.Build.Utilities.Task>, vous pouvez utiliser n'importe quelle méthode d'assistance parmi les suivantes sur la classe <xref:Microsoft.Build.Utilities.Task> pour déclencher des événements qui seront interceptés et affichés par tous les journaux inscrits :  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Si votre tâche implémente <xref:Microsoft.Build.Framework.ITask> directement, vous pouvez tout de même déclencher des événements de ce type mais vous devez utiliser l'interface IBuildEngine.  L'exemple suivant montre une tâche qui implémente ITask et déclenche un événement personnalisé :  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## Imposer la définition de paramètres de tâche  
 Vous pouvez marquer certaines propriétés de tâche comme « requises » de sorte que tout fichier projet, qui exécute la tâche, doive définir des valeurs pour ces propriétés afin que la génération réussisse.  Appliquez l'attribut `[Required]` à la propriété .NET dans votre tâche comme suit :  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 L'attribut `[Required]` est défini par <xref:Microsoft.Build.Framework.RequiredAttribute> dans l'espace de noms <xref:Microsoft.Build.Framework>.  
  
## Exemple  
  
### Description  
 La classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] suivante montre une tâche qui dérive de la classe d'assistance <xref:Microsoft.Build.Utilities.Task>.  Cette tâche retourne `true`, indiquant qu'elle a réussi.  
  
### Code  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Exemple  
  
### Description  
 La classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] suivante montre une tâche qui implémente l'interface <xref:Microsoft.Build.Framework.ITask>.  Cette tâche retourne `true`, indiquant qu'elle a réussi.  
  
### Code  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Exemple  
  
### Description  
 Cette classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] montre une tâche qui dérive de la classe d'assistance <xref:Microsoft.Build.Utilities.Task>.  Elle possède une propriété de type chaîne requise, et déclenche un événement qui est affiché par tous les journaux inscrits.  
  
### Code  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## Exemple  
  
### Description  
 L'exemple suivant montre un fichier projet qui appelle l'exemple de tâche précédent, SimpleTask3.  
  
### Code  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)