---
title: Écriture de tâches | Microsoft Docs
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
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4b15434c75fb4cd2a295789794f6c9f8eb882bb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254890"
---
# <a name="task-writing"></a>Écriture de tâches
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Les tâches fournissent le code exécuté pendant le processus de génération. Les tâches sont contenues dans les cibles. Une bibliothèque de tâches types est incluse dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. De plus, vous pouvez créer vos propres tâches. Pour plus d’informations sur la bibliothèque de tâches incluse dans [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], consultez [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Tâches  
 Voici quelques exemples de tâches : [Copy](../msbuild/copy-task.md), qui copie des fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée des répertoires et [Csc](../msbuild/csc-task.md), qui compile des fichiers de code source [!INCLUDE[csprcs](../includes/csprcs-md.md)]. Chaque tâche est implémentée en tant que classe .NET implémentant l’interface <xref:Microsoft.Build.Framework.ITask>, définie dans l’assembly Microsoft.Build.Framework.dll.  
  
 Vous pouvez adopter deux approches lors de l’implémentation d’une tâche :  
  
-   implémenter directement l’interface <xref:Microsoft.Build.Framework.ITask> ;  
  
-   dériver votre classe de la classe d’assistance, <xref:Microsoft.Build.Utilities.Task>, définie dans l’assembly Microsoft.Build.Utilities.dll. La tâche implémente ITask et fournit des implémentations par défaut de certains membres ITask. De plus, la journalisation est plus facile.  
  
 Dans les deux cas, vous devez ajouter à votre classe une méthode nommée `Execute`, qui est la méthode appelée lorsque la tâche s’exécute. Cette méthode n’accepte aucun paramètre et retourne une valeur `Boolean` : `true` si la tâche a réussi ou `false` si elle a échoué. L’exemple suivant montre une tâche qui n’effectue aucune action et retourne `true`.  
  
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
  
 Le fichier projet suivant exécute cette tâche :  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Lorsque les tâches sont exécutées, elles peuvent également recevoir des entrées du fichier projet si vous créez des propriétés .NET dans la classe de tâche. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] définit ces propriétés immédiatement avant l’appel de la méthode `Execute` de la tâche. Pour créer une propriété de type chaîne, utilisez du code de tâche tel que celui-ci :  
  
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
  
 Le fichier projet suivant exécute cette tâche et définit `MyProperty` sur la valeur donnée :  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Inscription de tâches  
 Si un projet va exécuter une tâche, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] doit savoir comment localiser l’assembly qui contient la classe de tâche. Les tâches sont inscrites à l’aide de [l’élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 Le fichier [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Microsoft.Common.Tasks est un fichier projet qui contient une liste d’éléments `UsingTask` qui inscrivent toutes les tâches fournies avec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Ce fichier est inclus automatiquement lors de la génération de chaque projet. Si une tâche inscrite dans Microsoft.Common.Tasks est également inscrite dans le fichier projet actuel, ce dernier est prioritaire. Autrement dit, vous pouvez remplacer une tâche par défaut par votre propre tâche de même nom.  
  
> [!TIP]
>  Vous pouvez voir la liste des tâches qui sont fournies avec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] en affichant le contenu de Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Déclenchement d’événements à partir d’une tâche  
 Si votre tâche dérive de la classe d’assistance <xref:Microsoft.Build.Utilities.Task>, vous pouvez utiliser l’une des méthodes d’assistance suivantes dans la classe <xref:Microsoft.Build.Utilities.Task> pour déclencher des événements qui seront interceptés et affichés par tous les journaux inscrits :  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Si votre tâche implémente <xref:Microsoft.Build.Framework.ITask> directement, vous pouvez également déclencher ces événements, mais vous devez pour cela utiliser l’interface IBuildEngine. L’exemple suivant montre une tâche qui implémente ITask et déclenche un événement personnalisé :  
  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>Exiger la définition de paramètres de tâche  
 Vous pouvez marquer certaines propriétés de tâche comme étant « obligatoires ». De cette façon, si les fichiers projet qui exécutent la tâche ne définissent pas les valeurs de ces propriétés, la génération échoue. Dans votre tâche, appliquez l’attribut `[Required]` à la propriété .NET de la manière suivante :  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 L’attribut `[Required]` est défini par <xref:Microsoft.Build.Framework.RequiredAttribute> dans l’espace de noms <xref:Microsoft.Build.Framework>.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 La classe [!INCLUDE[csprcs](../includes/csprcs-md.md)] suivante montre une tâche qui dérive de la classe d’assistance <xref:Microsoft.Build.Utilities.Task>. Cette tâche retourne `true`, ce qui indique qu’elle a réussi.  
  
### <a name="code"></a>Code  
  
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
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 La classe [!INCLUDE[csprcs](../includes/csprcs-md.md)] suivante montre une tâche qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. Cette tâche retourne `true`, ce qui indique qu’elle a réussi.  
  
### <a name="code"></a>Code  
  
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
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 La classe [!INCLUDE[csprcs](../includes/csprcs-md.md)] montre une tâche qui dérive de la classe d’assistance <xref:Microsoft.Build.Utilities.Task>. Elle comprend une propriété de type chaîne obligatoire, et déclenche un événement qui est affiché par tous les journaux inscrits.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre un fichier projet qui appelle l’exemple de tâche précédent (SimpleTask3).  
  
### <a name="code"></a>Code  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



