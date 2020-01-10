---
title: 'Procédure pas à pas : création d’une tâche inline | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3856c658c4d3d2598b69cc9bf77f95c219b187b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590044"
---
# <a name="walkthrough-create-an-inline-task"></a>Procédure pas à pas : Créer une tâche inline
Les tâches MSBuild sont généralement créées en compilant une classe qui implémente l’interface <xref:Microsoft.Build.Framework.ITask>. À compter du .NET Framework version 4, vous pouvez créer des tâches inline dans le fichier projet. Vous n’êtes pas obligé de créer un assembly séparé pour héberger la tâche. Pour plus d’informations, voir [Tâches inline](../msbuild/msbuild-inline-tasks.md).

 Cette procédure pas à pas montre comment créer et exécuter les tâches inline suivantes :

- Tâche qui n’a pas de paramètres d’entrée ou de sortie.

- Tâche avec un paramètre d’entrée et aucun paramètre de sortie.

- Tâche avec deux paramètres d’entrée et un paramètre de sortie qui retourne une propriété MSBuild.

- Tâche avec deux paramètres d’entrée et un paramètre de sortie qui retourne un élément MSBuild.

Pour créer et exécuter les tâches, utilisez Visual Studio et la **fenêtre d’invite de commandes Visual Studio** comme suit :

1. Créez un fichier projet MSBuild à l’aide de Visual Studio.

2. Modifiez le fichier projet dans Visual Studio pour créer la tâche inline.

3. Utilisez la **fenêtre d’invite de commandes** pour générer le projet et examiner les résultats.

## <a name="create-and-modify-an-msbuild-project"></a>Créer et modifier un projet MSBuild
 Le système de projet Visual Studio est basé sur MSBuild. Vous pouvez donc créer un fichier projet de build à l’aide de Visual Studio. Dans cette section, vous créez un fichier projet Visual C#. (Vous pouvez créer à la place un fichier projet Visual Basic. Dans le contexte de ce didacticiel, la différence entre les deux fichiers projet est mineure.)

#### <a name="to-create-and-modify-a-project-file"></a>Pour créer et modifier un fichier projet

1. Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le type de projet **Visual C#** , puis le modèle **Application Windows Forms**. Dans la zone **Nom**, tapez `InlineTasks`. Tapez un **Emplacement** pour la solution, par exemple, *D:\\* . Vérifiez que l’option **Créer un répertoire pour la solution** est sélectionnée, que l’option **Ajouter au contrôle de code source** ne l’est pas et que **Nom de solution** correspond à **InlineTasks**.

3. Cliquez sur **OK** pour créer le fichier projet.

3. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **InlineTasks**, puis sur **Décharger le projet**.

4. Recliquez avec le bouton droit sur le nœud du projet, puis cliquez sur **Modifier BuildApp.csproj**.

     Le fichier projet s’affiche dans l’éditeur de code.

## <a name="add-a-basic-hello-task"></a>Ajouter une tâche Hello de base
 À présent, ajoutez au fichier projet une tâche de base qui affiche le message « Hello, world! ». Ajoutez également une cible TestBuild par défaut pour appeler la tâche.

#### <a name="to-add-a-basic-hello-task"></a>Ajouter une tâche Hello de base

1. Dans le nœud `Project` racine, remplacez l’attribut `DefaultTargets` par `TestBuild`. Le nœud `Project` résultant doit ressembler à ce qui suit :

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Ajoutez la cible et la tâche inline suivantes au fichier projet juste avant la balise `</Project>`.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage("Hello, world!", MessageImportance.High);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Enregistrez le fichier projet.

   Ce code crée une tâche Inline nommée Hello et n’a pas de paramètres, de références ou de directives de `Using`. La tâche Hello contient une seule ligne de code, qui affiche un message de type Hello sur l’appareil de journalisation par défaut, généralement la fenêtre de console.

### <a name="run-the-hello-task"></a>Exécuter la tâche Hello
 Exécutez MSBuild à l’aide de la **fenêtre d’invite de commandes** pour construire la tâche Hello et traiter la cible TestBuild qui l’appelle.

##### <a name="to-run-the-hello-task"></a>Pour exécuter la tâche Hello

1. Cliquez sur **Démarrer**, sur **Tous les programmes**, puis recherchez le dossier **Visual Studio Tools** et cliquez sur **Invite de commandes Visual Studio**.

2. Dans la **Fenêtre d’invite de commandes**, recherchez le dossier contenant le fichier projet (dans ce cas, *D:\InlineTasks\InlineTasks\\* ).

3. Tapez **msbuild** sans commutateurs de commande, puis appuyez sur **Entrée**. Par défaut, cette commande génère le fichier *InlineTasks.csproj* et traite la cible par défaut TestBuild, qui appelle la tâche Hello.

4. Examinez la sortie dans la **fenêtre d’invite de commandes**. Vous devez normalement voir cette ligne :

    `Hello, world!`

   > [!NOTE]
   > Si vous ne voyez pas le message Hello, essayez de réenregistrer le fichier projet puis d’exécuter la tâche Hello.

   En alternant entre l’éditeur de code et la **fenêtre d’invite de commandes**, vous pouvez modifier le fichier projet et voir rapidement les résultats.

## <a name="define-the-echo-task"></a>Définir la tâche Echo
 Créez une tâche inline qui accepte un paramètre de chaîne et affiche la chaîne sur l’appareil de journalisation par défaut.

#### <a name="to-define-the-echo-task"></a>Pour définir la tâche Echo

1. Dans l’éditeur de code, remplacez la tâche Hello et la cible TestBuild par le code suivant.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(Text, MessageImportance.High);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. Dans la **Fenêtre d’invite de commandes**, tapez **msbuild** sans commutateurs de commande, puis appuyez sur **Entrée**. Par défaut, cette commande traite la cible par défaut TestBuild, qui appelle la tâche Echo.

3. Examinez la sortie dans la **fenêtre d’invite de commandes**. Vous devez normalement voir cette ligne :

    `Greetings!`

   Ce code définit une tâche inline nommée Echo avec un seul paramètre d’entrée Text obligatoire. Par défaut, les paramètres sont de type System.String. La valeur du paramètre Text est définie quand la cible TestBuild appelle la tâche Echo.

## <a name="define-the-adder-task"></a>Définir la tâche Adder
 Créez une tâche inline qui ajoute deux paramètres entiers et émet leur somme comme propriété MSBuild.

#### <a name="to-define-the-adder-task"></a>Pour définir la tâche Adder

1. Dans l’éditeur de code, remplacez la tâche Echo et la cible TestBuild par le code suivant.

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. Dans la **Fenêtre d’invite de commandes**, tapez **msbuild** sans commutateurs de commande, puis appuyez sur **Entrée**. Par défaut, cette commande traite la cible par défaut TestBuild, qui appelle la tâche Echo.

3. Examinez la sortie dans la **fenêtre d’invite de commandes**. Vous devez normalement voir cette ligne :

    `The sum is 9`

   Ce code définit une tâche inline nommée Adder avec deux paramètres d’entrée de type entier obligatoires, A et B, et un paramètre de sortie entier, C. La tâche Adder ajoute les deux paramètres d’entrée et retourne la somme dans le paramètre de sortie. La somme est émise en tant que propriété MSBuild `Sum`. Les valeurs des paramètres d’entrée sont définies quand la cible TestBuild appelle la tâche Adder.

## <a name="define-the-regx-task"></a>Définir la tâche RegX
 Créez une tâche inline qui accepte un groupe d’éléments et une expression régulière, et retourne la liste de tous les éléments dont le contenu du fichier correspond à l’expression.

#### <a name="to-define-the-regx-task"></a>Pour définir la tâche RegX

1. Dans l’éditeur de code, remplacez la tâche Adder et la cible TestBuild par le code suivant.

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. Dans la **Fenêtre d’invite de commandes**, tapez **msbuild** sans commutateurs de commande, puis appuyez sur **Entrée**. Par défaut, cette commande traite la cible par défaut TestBuild, qui appelle la tâche RegX.

3. Examinez la sortie dans la **fenêtre d’invite de commandes**. Vous devez normalement voir ces lignes :

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Ce code définit une tâche inline nommée RegX avec les trois paramètres suivants :

- `Expression` est un paramètre d’entrée de chaîne obligatoire dont la valeur est l’expression régulière à mettre en correspondance. Dans cet exemple, l’expression correspond au mot « public » ou « protected ».

- `Files` est un paramètre d’entrée de liste d’éléments obligatoire dont la valeur est une liste de fichiers dans laquelle la recherche d’une correspondance a lieu. Dans cet exemple, `Files` a pour valeur l’élément `Compile`, qui répertorie les fichiers sources du projet.

- `Result` est un paramètre de sortie qui a pour valeur la liste des fichiers dont le contenu correspond à l’expression régulière.

  Les valeurs des paramètres d’entrée sont définies quand la cible TestBuild appelle la tâche RegX. La tâche RegX lit chaque fichier et retourne la liste des fichiers qui correspondent à l’expression régulière. Cette liste est retournée sous la forme du paramètre de sortie `Result`, qui est émis en tant qu’élément MSBuild `MatchedFiles`.

### <a name="handle-reserved-characters"></a>Gérer les caractères réservés
 L’analyseur MSBuild traite les tâches inline au format XML. Les caractères qui ont une signification réservée au format XML, par exemple « \< » et « > », sont détectés et gérés comme s’il s’agissait de code XML, et non de code source .NET. Pour inclure les caractères réservés dans des expressions de code telles que `Files.Length > 0`, écrivez l’élément `Code` de telle sorte que son contenu figure dans une expression CDATA, comme suit :

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  // Your code goes here.

  ]]>
</Code>
```

## <a name="see-also"></a>Voir aussi
- [Tâches inline](../msbuild/msbuild-inline-tasks.md)
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
- [Cibles MSBuild](../msbuild/msbuild-targets.md)
