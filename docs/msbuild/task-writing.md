---
title: Écriture de tâches | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cbcf47ec83e1b900ba94ab3842c2cfa63fdcc5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631834"
---
# <a name="task-writing"></a>Écriture de tâches

Les tâches fournissent le code exécuté pendant le processus de génération. Les tâches sont contenues dans les cibles. Une bibliothèque de tâches typiques est incluse avec MSBuild, et vous pouvez également créer vos propres tâches. Pour plus d’informations sur la bibliothèque des tâches qui sont incluses avec MSBuild, voir [référence De tâche](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Tâches

 Parmi les exemples de tâches, citons [Copy](../msbuild/copy-task.md), qui copie un ou plusieurs fichiers, [MakeDir](../msbuild/makedir-task.md), qui crée un répertoire, et [Csc](../msbuild/csc-task.md), qui compile les fichiers de code source C. Chaque tâche est implémentée en tant que classe .NET implémentant l’interface <xref:Microsoft.Build.Framework.ITask>, définie dans l’assembly *Microsoft.Build.Framework.dll*.

 Vous pouvez adopter deux approches lors de l’implémentation d’une tâche :

- implémenter directement l’interface <xref:Microsoft.Build.Framework.ITask> ;

- dériver votre classe de la classe d’assistance, <xref:Microsoft.Build.Utilities.Task>, définie dans l’assembly *Microsoft.Build.Utilities.dll*. La tâche implémente ITask et fournit des implémentations par défaut de certains membres ITask. De plus, la journalisation est plus facile.

Dans les deux cas, vous devez ajouter à votre classe une méthode nommée `Execute`, qui est la méthode appelée lorsque la tâche s’exécute. Cette méthode n’accepte aucun paramètre et retourne une valeur `Boolean` : `true` si la tâche a réussi ou `false` si elle a échoué. L’exemple suivant montre une tâche qui n’effectue aucune action et retourne `true`.

```csharp
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

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Lorsque les tâches sont exécutées, elles peuvent également recevoir des entrées du fichier projet si vous créez des propriétés .NET dans la classe de tâche. MSBuild définit ces propriétés immédiatement `Execute` avant d’appeler la méthode de la tâche. Pour créer une propriété de type chaîne, utilisez du code de tâche tel que celui-ci :

```csharp
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

        public string MyProperty { get; set; }
    }
}
```

 Le fichier projet suivant exécute cette tâche et définit `MyProperty` sur la valeur donnée :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Inscrire des tâches

 Si un projet doit exécuter une tâche, MSBuild doit savoir comment localiser l’assemblage qui contient la classe de tâches. Les tâches sont inscrites à l’aide de [l’élément UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Le fichier MSBuild *Microsoft.Common.Tasks* est un fichier `UsingTask` de projet qui contient une liste d’éléments qui enregistrent toutes les tâches qui sont fournies avec MSBuild. Ce fichier est inclus automatiquement lors de la génération de chaque projet. Si une tâche inscrite dans *Microsoft.Common.Tasks* est également inscrite dans le fichier projet actuel, ce dernier est prioritaire. Autrement dit, vous pouvez remplacer une tâche par défaut par votre propre tâche du même nom.

> [!TIP]
> Vous pouvez voir une liste des tâches qui sont fournies avec MSBuild en visualisant le contenu de *Microsoft.Common.Tasks*.

## <a name="raise-events-from-a-task"></a>Déclencher des événements à partir d’une tâche

 Si votre tâche dérive de la classe d’assistance <xref:Microsoft.Build.Utilities.Task>, vous pouvez utiliser l’une des méthodes d’assistance suivantes dans la classe <xref:Microsoft.Build.Utilities.Task> pour déclencher des événements qui seront interceptés et affichés par tous les journaux inscrits :

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Si votre tâche implémente <xref:Microsoft.Build.Framework.ITask> directement, vous pouvez également déclencher ces événements, mais vous devez pour cela utiliser l’interface IBuildEngine. L’exemple suivant montre une tâche qui implémente ITask et déclenche un événement personnalisé :

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

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

## <a name="require-task-parameters-to-be-set"></a>Exiger la définition de paramètres de tâche

 Vous pouvez marquer certaines propriétés de tâche comme étant « obligatoires ». De cette façon, si les fichiers projet qui exécutent la tâche ne définissent pas les valeurs de ces propriétés, la génération échoue. Dans votre tâche, appliquez l’attribut `[Required]` à la propriété .NET de la manière suivante :

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 L’attribut `[Required]` est défini par <xref:Microsoft.Build.Framework.RequiredAttribute> dans l’espace de noms <xref:Microsoft.Build.Framework>.

## <a name="how-msbuild-invokes-a-task"></a>Comment MSBuild invoque une tâche

Lors de l’invocation d’une tâche, MSBuild a d’abord instantané la classe de tâches, puis appelle les ensembles de propriété de cet objet pour les paramètres de tâches qui sont définis dans l’élément de tâche dans le fichier de projet. Si l’élément de tâche ne spécifie pas un paramètre, ou si l’expression spécifiée dans l’élément évalue à une chaîne vide, le setter de propriété n’est pas appelé.

Par exemple, dans le projet

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

seul le setter pour `Input3` est appelé.

Une tâche ne doit pas dépendre d’un ordre relatif de l’invocation de la propriété par paramètres.

### <a name="task-parameter-types"></a>Types de paramètres de tâche

Le MSBuild gère nativement `string`les `bool` `ITaskItem` propriétés de type, , et `ITaskItem[]`. Si une tâche accepte un paramètre d’un type <xref:System.Convert.ChangeType%2A> différent, `string` MSBuild invoque à convertir (avec toutes les références de propriété et d’article élargi) au type de destination. Si la conversion échoue pour n’importe quel paramètre d’entrée, MSBuild émet une erreur et n’appelle pas la méthode de `Execute()` la tâche.

## <a name="example"></a> Exemple

### <a name="description"></a>Description

Cette classe suivante C ' démontre une <xref:Microsoft.Build.Utilities.Task> tâche dérivée de la classe d’aide. Cette tâche retourne `true`, ce qui indique qu’elle a réussi.

### <a name="code"></a>Code

```csharp
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

## <a name="example"></a> Exemple

### <a name="description"></a>Description

Cette classe suivante C ' démontre <xref:Microsoft.Build.Framework.ITask> une tâche de mise en œuvre de l’interface. Cette tâche retourne `true`, ce qui indique qu’elle a réussi.

### <a name="code"></a>Code

```csharp
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
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example"></a> Exemple

### <a name="description"></a>Description

Cette classe CMD démontre une tâche <xref:Microsoft.Build.Utilities.Task> qui découle de la classe d’aide. Elle comprend une propriété de type chaîne obligatoire, et déclenche un événement qui est affiché par tous les journaux inscrits.

### <a name="code"></a>Code

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a> Exemple

### <a name="description"></a>Description

L’exemple suivant montre un fichier projet qui appelle l’exemple de tâche précédent (SimpleTask3).

### <a name="code"></a>Code

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
