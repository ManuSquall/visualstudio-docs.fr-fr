---
title: L’accès à des modèles à partir de modèles de texte | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3162350a9afbe7972c4e593049141f533517bdc3
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="accessing-models-from-text-templates"></a>Accès aux modèles depuis des modèles de texte
À l’aide de modèles de texte, vous pouvez créer des fichiers de rapports, les fichiers de code source et les autres fichiers de texte qui sont basées sur des modèles de langage spécifique à un domaine. Pour plus d’informations de base sur les modèles de texte, consultez [génération de Code et les modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md). Les modèles de texte fonctionnent en mode expérimental lorsque vous déboguez votre DSL et fonctionnent également sur un ordinateur sur lequel vous avez déployé la DSL.  
  
> [!NOTE]
>  Lorsque vous créez une solution DSL, l’exemple de modèle de texte  **\*.tt** fichiers sont générés dans le projet de débogage. Lorsque vous modifiez les noms des classes de domaine, ces modèles ne fonctionnera plus. Néanmoins, ils incluent les directives de base dont vous avez besoin et fournissent des exemples que vous pouvez mettre à jour pour correspondre à votre DSL.  
  
 Pour accéder à un modèle à partir d’un modèle de texte :  
  
-   Définir la propriété d’héritage de la directive de modèle <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Cela permet d’accéder au magasin.  
  
-   Spécifiez les processeurs de directive pour la DSL que vous souhaitez accéder. Cela charge les assemblys de votre DSL afin que vous puissiez utiliser ses classes de domaine, les propriétés et les relations dans le code de votre modèle de texte. Il charge également le fichier de modèle que vous spécifiez.  
  
 A `.tt` fichier similaire à l’exemple suivant est créé dans le projet de débogage lorsque vous créez un nouveau [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution à partir du modèle de langage minimale DSL.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Notez les points suivants concernant ce modèle :  
  
-   Le modèle peut utiliser les classes de domaine, les propriétés et les relations que vous avez définie dans la définition DSL.  
  
-   Le modèle de charge le fichier de modèle que vous spécifiez dans le `requires` propriété.  
  
-   Une propriété dans `this` contient l’élément racine. À partir de là, votre code peut accéder à d’autres éléments du modèle. Le nom de la propriété est généralement identique à la classe de domaine racine de votre DSL. Dans cet exemple, il s’agit de `this.ExampleModel`.  
  
-   Bien que le langage dans lequel sont écrits les fragments de code c#, vous pouvez générer le texte de tout type. Vous pouvez également écrire du code [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en ajoutant la propriété `language="VB"` à le `template` la directive.  
  
-   Pour déboguer le modèle, ajoutez `debug="true"` à le `template` la directive. Le modèle s’ouvre dans une autre instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si une exception se produit. Si vous souhaitez arrêter dans le débogueur à un moment spécifique dans le code, insérez l’instruction `System.Diagnostics.Debugger.Break();`  
  
     Pour plus d’informations, consultez [débogage d’un modèle de texte T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Sur le processeur de directive DSL  
 Le modèle peut utiliser les classes de domaine que vous avez définie dans la définition de votre DSL. Cela est généré par une directive qui apparaît généralement au début du modèle. Dans l’exemple précédent, il est la suivante.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Le nom de la directive ( `MyLanguage`, dans cet exemple) est dérivé du nom de votre DSL. Il appelle une *processeur de directive* qui est générée dans le cadre de votre DSL. Vous pouvez trouver le code source dans **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 Le processeur de directive DSL effectue deux tâches principales :  
  
-   Il insère efficacement des directives d’assembly et d’importation dans le modèle qui fait référence à votre DSL. Cela vous permet d’utiliser des classes de votre domaine dans le code du modèle.  
  
-   Il charge le fichier que vous spécifiez dans le `requires` paramètre et définit une propriété `this` qui fait référence à l’élément racine du modèle chargé.  
  
## <a name="validating-the-model-before-running-the-template"></a>Avant d’exécuter le modèle de validation du modèle  
 Vous pouvez provoquer le modèle à valider avant que le modèle est exécuté.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Notez que :  
  
1.  Le `filename` et `validation` paramètres sont séparés par « ; » et il ne doit y avoir aucun autre séparateurs ou des espaces.  
  
2.  La liste des catégories de validation détermine les méthodes de validation sont exécutées. Plusieurs catégories doivent être séparés par «&#124;» et il ne doit y avoir aucun autre séparateurs ou des espaces.  
  
 Si une erreur est détectée, elle sera signalée dans la fenêtre d’erreurs, et le fichier de résultats contiendra un message d’erreur.  
  
##  <a name="Multiple"></a> L’accès à plusieurs modèles à partir d’un modèle de texte  
  
> [!NOTE]
>  Cette méthode vous permet de lire plusieurs modèles dans le même modèle, mais ne prend pas en charge les références ModelBus. Pour lire des modèles qui sont reliées par leurs références de ModelBus, consultez [à l’aide de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Si vous souhaitez accéder à plus d’un modèle à partir du même modèle de texte, vous devez appeler le processeur de directive généré une fois pour chaque modèle. Vous devez spécifier le nom de fichier de chaque modèle dans le `requires` paramètre. Vous devez spécifier les noms que vous souhaitez utiliser pour la classe de domaine racine dans le `provides` paramètre. Vous devez spécifier des valeurs différentes pour le `provides` paramètres dans chacun des appels de directive. Par exemple, supposons que vous disposez de trois fichiers de modèle appelés Library.xyz, School.xyz et Work.xyz. Pour y accéder à partir du même modèle de texte, vous devez écrire trois appels de directive qui ressemblent à celles ci-dessous.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Cet exemple de code est d’une langue qui est basée sur le modèle de solution de langage minimale.  
  
 Pour accéder aux modèles dans votre modèle de texte, vous pouvez maintenant écrire du code semblable au code dans l’exemple suivant.  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>Chargement des modèles de manière dynamique  
 Si vous souhaitez déterminer, lors de l’exécution, les modèles de charge, vous pouvez charger dynamiquement un fichier de modèle dans votre code de programme, au lieu d’utiliser la directive DSL spécifiques.  
  
 Toutefois, l’une des fonctions de la directive DSL spécifique est pour importer l’espace de noms DSL, afin que le code du modèle peut utiliser les classes de domaine définies dans ce DSL. Étant donné que vous n’utilisez pas la directive, vous devez ajouter  **\<assembly >** et  **\<Importer >** directives pour tous les modèles que vous pouvez charger. C’est facile si les différents modèles que vous pouvez charger sont toutes les instances de la même DSL.  
  
 Pour charger le fichier, la méthode la plus efficace est à l’aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. Dans ce scénario, votre modèle de texte utilise une directive DSL spécifiques pour charger le premier modèle de manière habituelle. Ce modèle contient des références de ModelBus à un autre modèle. Vous pouvez utiliser ModelBus pour ouvrir le modèle référencé et accéder à un élément particulier. Pour plus d’informations, consultez [à l’aide de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Dans un scénario habituel inférieur, vous souhaiterez ouvrir un fichier de modèle pour lequel vous avez uniquement un nom de fichier, et qui ne peut pas être en cours [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet. Dans ce cas, vous pouvez ouvrir le fichier à l’aide de la technique décrite dans [Comment : ouvrir un modèle à partir du fichier de Code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Génération de plusieurs fichiers à partir d’un modèle  
 Si vous souhaitez générer plusieurs fichiers - par exemple, pour générer un fichier distinct pour chaque élément dans un modèle, il existe plusieurs approches possibles. Par défaut, un seul fichier est généré à partir de chaque fichier de modèle.  
  
### <a name="splitting-a-long-file"></a>Fractionnement d’un fichier long  
 Dans cette méthode, vous utilisez un modèle pour générer un seul fichier, séparé par un délimiteur. Puis vous fractionnez le fichier en parties. Il existe deux modèles, un pour générer le fichier unique et l’autre à fractionner.  
  
 **LoopTemplate.t4** génère le fichier unique long. Notez que son extension de fichier est « .t4 », car il ne doit pas traité directement lorsque vous cliquez sur **transformer tous les modèles**. Ce modèle prend un paramètre qui spécifie la chaîne de délimiteur qui sépare les segments :  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt` appelle `LoopTemplate.t4`et puis fractionne le fichier résultant en segments. Notez que ce modèle n’a pas à être un modèle de modélisation, car elle ne lit pas le modèle.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```