---
title: "Génération de code dans un processus de génération | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 518713302e4698105340fcffaf1698edecf96f76
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="code-generation-in-a-build-process"></a>Génération de code dans un processus de génération
[La transformation de texte](../modeling/code-generation-and-t4-text-templates.md) peut être appelé dans le cadre de la [processus de génération](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) d’un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution. Il existe des tâches de génération qui sont spécialisées pour la transformation de texte. Les tâches de génération T4 exécutent les modèles de texte au moment du design. En outre, elles compilent les modèles de texte (prétraités) au moment de l'exécution.  
  
 Il existe quelques différences en matière de possibilités offertes par les tâches de génération, selon le moteur de génération que vous utilisez. Lorsque vous générez la solution dans Visual Studio, un modèle de texte peut accéder à l’API Visual Studio (EnvDTE) si le [hostspecific = « true »](../modeling/t4-template-directive.md) attribut est défini. Mais qui n’est pas vrai lorsque vous générez la solution à partir de la ligne de commande ou lorsque vous démarrez une génération serveur via Visual Studio. Dans ces situations, la génération est exécutée par MSBuild et un autre hôte T4 est utilisé.  
  
 Cela signifie que vous ne peut pas accéder à éléments tels que les noms de fichiers de projet de la même manière lorsque vous générez un modèle de texte dans MSBuild. Toutefois, vous pouvez [passer des informations sur l’environnement dans les modèles de texte et les processeurs de directive à l’aide des paramètres de génération](#parameters).  
  
##  <a name="buildserver"></a>Configurer vos ordinateurs  
 Pour activer les tâches de génération sur votre ordinateur de développement, installer le Kit de développement logiciel de modélisation pour Visual Studio.
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

 Si [votre serveur de builds](http://msdn.microsoft.com/Library/788443c3-0547-452e-959c-4805573813a9) s’exécute sur un ordinateur sur lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est ne pas installé, copiez les fichiers suivants à l’ordinateur de build à partir de votre ordinateur de développement. Remplacer les numéros de version plus récente de ' *'.  
  
-   $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating  
  
    -   Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll  
  
    -   Microsoft.TextTemplating.Build.Tasks.dll  
  
    -   Microsoft.TextTemplating.targets  
  
-   $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0  
  
    -   Microsoft.VisualStudio.TextTemplating.*.0.dll  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (plusieurs fichiers)  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll  
  
-   $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll  
  
## <a name="to-edit-the-project-file"></a>Pour modifier le fichier projet  
 Vous devrez modifier votre fichier projet pour configurer certaines des fonctionnalités dans MSBuild.  
  
 Dans l’Explorateur de solutions, choisissez **Unload** dans le menu contextuel de votre projet. Cela vous permet de modifier le fichier .csproj ou .vbproj dans l'éditeur XML.  
  
 Lorsque vous avez terminé, choisissez **recharger**.  
  
## <a name="import-the-text-transformation-targets"></a>Importation des cibles de la transformation de texte  
 Dans le fichier .vbproj ou .csproj, recherchez une ligne telle que :  
  
 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`  
  
 \- ou -  
  
 `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`  
  
 Après cette ligne, insérez l'importation de modèles de texte :  
  
```xml  
<!-- Optionally make the import portable across VS versions -->  
  <PropertyGroup>  
    <!-- Get the Visual Studio version - defaults to 10: -->  
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>  
    <!-- Keep the next element all on one line: -->  
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>  
  </PropertyGroup>  
  
<!-- This is the important line: -->  
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />  
```  
  
## <a name="transforming-templates-in-a-build"></a>Transformation des modèles d'une build  
 Il existe des propriétés que vous pouvez insérer dans votre fichier projet afin de contrôler la tâche de transformation :  
  
-   Exécutez la tâche de transformation au début de chaque génération :  
  
    ```xml  
    <PropertyGroup>  
        <TransformOnBuild>true</TransformOnBuild>  
    </PropertyGroup>  
    ```  
  
-   Remplacez les fichiers en lecture seule, par exemple, car ils ne sont pas vérifiés :  
  
    ```xml  
    <PropertyGroup>  
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>  
    </PropertyGroup>  
    ```  
  
-   Transformez chaque modèle à chaque fois :  
  
    ```xml  
    <PropertyGroup>  
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>  
    </PropertyGroup>  
    ```  
  
     Par défaut, la tâche T4 MSBuild régénère un fichier de sortie s'il est antérieur à son fichier modèle, aux fichiers inclus ou aux fichiers qui ont été précédemment lus par le modèle ou par un processeur de directive qu'il utilise. Notez qu'il s'agit d'un test de dépendance beaucoup plus puissant que celui de la commande Transformer tous les modèles dans Visual Studio. Ce dernier ne fait que comparer les dates du fichier modèle et du fichier de sortie.  
  
 Pour exécuter uniquement les transformations de texte dans votre projet, appelez la tâche TransformAll :  
  
 `msbuild myProject.csproj /t:TransformAll`  
  
 Pour transformer un modèle de texte spécifique :  
  
 `msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`  
  
 Vous pouvez utiliser des caractères génériques dans TransformFile :  
  
 `msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`  
  
## <a name="source-control"></a>Contrôle de code source  
 Il n'existe aucune intégration prédéfinie spécifique avec un système de contrôle de code source. Toutefois, vous pouvez ajouter vos propres extensions, par exemple pour extraire et archiver un fichier généré. Par défaut, la tâche de transformation de texte évite de remplacer un fichier en lecture seule. Lorsqu'un tel fichier est trouvé, une erreur est journalisée dans la liste d'erreurs de Visual Studio, et la tâche échoue.  
  
 Pour spécifier que les fichiers en lecture seule doivent être remplacés, insérez la propriété suivante :  
  
 `<OverwriteReadOnlyOuputFiles>true</OverwriteReadOnlyOuputFiles>`  
  
 À moins que vous ne personnalisiez l'étape de post-traitement, un avertissement sera consigné dans la liste d'erreurs lorsqu'un fichier est remplacé.  
  
## <a name="customizing-the-build-process"></a>Personnalisation du processus de génération  
 La transformation de texte se produit avant les autres tâches du processus de génération. Pour définir les tâches appelées avant et après la transformation, définissez les propriétés `$(BeforeTransform)` et `$(AfterTransform)` :  
  
```  
<PropertyGroup>  
    <BeforeTransform>CustomPreTransform</BeforeTransform>  
    <AfterTransform>CustomPostTransform</AfterTransform>  
  </PropertyGroup>  
  <Target Name="CustomPreTransform">  
    <Message Text="In CustomPreTransform..." Importance="High" />  
  </Target>  
  <Target Name="CustomPostTransform">  
    <Message Text="In CustomPostTransform..." Importance="High" />  
  </Target>  
```  
  
 Dans `AfterTransform`, vous pouvez référencer des listes de fichiers :  
  
-   GeneratedFiles : liste des fichiers écrits par le processus. Pour les fichiers qui ont remplacé des fichiers en lecture seule existants, %(GeneratedFiles.ReadOnlyFileOverwritten) a la valeur true. Ces fichiers peuvent être extraits du contrôle de code source.  
  
-   NonGeneratedFiles : liste des fichiers en lecture seule qui n'ont pas été remplacés.  
  
 Par exemple, vous définissez une tâche afin d'extraire GeneratedFiles.  
  
## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath et OutputFileName  
 Ces propriétés sont utilisées uniquement par MSBuild. Elles n'affectent pas la génération du code dans Visual Studio. Elles redirigent le fichier de sortie généré vers un autre dossier ou fichier. Le dossier cible doit déjà exister.  
  
```xml  
<ItemGroup>  
  <None Include="MyTemplate.tt">  
    <Generator>TextTemplatingFileGenerator</Generator>  
    <OutputFilePath>MyFolder</OutputFilePath>  
    <LastGenOutput>MyTemplate.cs</LastGenOutput>  
  </None>  
</ItemGroup>  
```  
  
 `$(IntermediateOutputPath).` est un dossier utile pour la redirection  
  
 Si vous spécifiez un nom de fichier de sortie, il est prioritaire par rapport à l’extension spécifiée dans la directive de sortie des modèles.  
  
```xml  
<ItemGroup>  
  <None Include="MyTemplate.tt">  
    <Generator>TextTemplatingFileGenerator</Generator>  
    <OutputFileName>MyOutputFileName.cs</OutputFileName>  
    <LastGenOutput>MyTemplate.cs</LastGenOutput>  
  </None>  
</ItemGroup>  
```  
  
 N’est pas recommandé de spécifier OutputFileName ou OutputFilePath si vous transformez également des modèles dans Visual Studio à l’aide de la transformer tous les ou le Générateur de fichier unique en cours d’exécution. Vous obtiendrez des chemins d’accès de fichiers distincts selon la façon dont vous avez déclenché la transformation. Cela peut vraiment prêter à confusion.  
  
## <a name="adding-reference-and-include-paths"></a>Ajout de chemins d'accès des références et Include  
 L'hôte possède un ensemble de chemins d'accès par défaut dans lesquels il recherche les assemblys référencés dans les modèles. Pour effectuer un ajout à cet ensemble :  
  
```  
<ItemGroup>  
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />  
    <!-- Add more T4ReferencePath items here -->  
</ItemGroup>  
```  
  
 Pour définir les dossiers où rechercher les fichiers Include, fournissez une liste d'éléments délimités par des points-virgules. Généralement, vous effectuez l’ajout à la liste des dossiers existants.  
  
```  
<PropertyGroup>  
    <IncludeFolders>  
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>  
</PropertyGroup>  
  
```  
  
##  <a name="parameters"></a>Passer des données de contexte de build dans les modèles  
 Vous pouvez définir des valeurs de paramètre dans le fichier projet. Par exemple, vous pouvez passer [générer](../msbuild/msbuild-properties.md) propriétés et [variables d’environnement](../msbuild/how-to-use-environment-variables-in-a-build.md):  
  
```xml  
<ItemGroup>  
  <T4ParameterValues Include="ProjectFolder">  
    <Value>$(ProjectDir)</Value>  
    <Visible>false</Visible>  
  </T4ParameterValues>  
</ItemGroup>  
```  
  
 Dans un modèle de texte, définissez `hostspecific` dans la directive de modèle. Utilisez le [paramètre](../modeling/t4-parameter-directive.md) directive pour obtenir des valeurs :  
  
```  
<#@template language="c#" hostspecific="true"#>  
<#@ parameter type="System.String" name="ProjectFolder" #>  
The project folder is: <#= ProjectFolder #>  
  
```  
  
 Dans un processeur de directive, vous pouvez appeler <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> :  
  
```csharp  
string value = Host.ResolveParameterValue("-", "-", "parameterName");  
```  
  
```vb  
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")  
```  
  
> [!NOTE]
>  `ResolveParameterValue` obtient des données uniquement à partir de `T4ParameterValues` lorsque vous utilisez MSBuild. Lorsque vous transformez le modèle à l'aide de Visual Studio, les paramètres ont des valeurs par défaut.  
  
##  <a name="msbuild"></a>À l’aide des propriétés du projet dans l’assembly et les directives #include  
 Les macros Visual Studio telles que $ (SolutionDir) ne fonctionnent pas dans MSBuild. Vous pouvez utiliser des propriétés de projet à la place.  
  
 Modifiez votre fichier projet .csproj ou .vbproj pour définir une propriété de projet. Cet exemple définit une propriété nommée `myLibFolder` :  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Désormais, vous pouvez utiliser votre propriété de projet dans les directives d'assembly et Include :  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>  
```  
  
 Ces directives obtiennent des valeurs à partir de T4parameterValues dans MSBuild et les hôtes Visual Studio.  
  
## <a name="q--a"></a>Questions et réponses  
 **Pourquoi voudrais-je transformer des modèles dans le serveur de builds ? J’ai déjà transformé des modèles dans Visual Studio avant d’archiver mon code.**  
  
 Si vous mettez à jour un fichier inclus ou tout autre fichier lu par le modèle, Visual Studio ne transforme pas le fichier automatiquement. La transformation des modèles de la build permet de s’assurer que tout est à jour.  
  
 **Ce que sont les autres options de transformation de modèles de texte ?**  
  
-   Le [utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) peut être utilisée dans les scripts de commande. Dans la plupart des cas, il est plus facile d’utiliser MSBuild.  
  
-   [Appel d’une transformation de texte dans une extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
  
-   [Les modèles de texte au moment du design](../modeling/design-time-code-generation-by-using-t4-text-templates.md) sont transformés par Visual Studio.  
  
-   [Exécuter des modèles de texte moment](../modeling/run-time-text-generation-with-t4-text-templates.md) sont transformés au moment de l’exécution de votre application.  
  
## <a name="read-more"></a>En lire plus  
 Vous trouverez de bons conseils dans le modèle T4 MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets  
  
 [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)  
  
 [Oleg Sych : Présentation de l’intégration T4:MSBuild](http://www.olegsych.com/2010/04/understanding-t4-msbuild-integration/)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

