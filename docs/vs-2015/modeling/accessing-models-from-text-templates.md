---
title: Accès aux modèles depuis des modèles de texte | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7ad3d921de04c3fd612571a55d012588793b91db
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257190"
---
# <a name="accessing-models-from-text-templates"></a>Accès aux modèles depuis des modèles de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

À l’aide de modèles de texte, vous pouvez créer des fichiers de rapport, les fichiers de code source et autres fichiers de texte basés sur les modèles de langage spécifique à un domaine. Pour plus d’informations de base sur les modèles de texte, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md). Les modèles de texte fonctionnent en mode expérimental lorsque vous déboguez votre DSL et fonctionnent également sur un ordinateur sur lequel vous avez déployé la solution DSL.  
  
> [!NOTE]
>  Lorsque vous créez une solution DSL, un exemple de modèle de texte  **\*.tt** fichiers sont générés dans le projet de débogage. Lorsque vous modifiez les noms des classes de domaine, ces modèles ne fonctionnera plus. Néanmoins, ils incluent les directives de base dont vous avez besoin et fournissent des exemples que vous pouvez mettre à jour pour correspondre à votre DSL.  
  
 Pour accéder à un modèle à partir d’un modèle de texte :  
  
-   Définissez la propriété d’hériter de la directive de modèle à <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Cela permet d’accéder à la Store.  
  
-   Spécifiez les processeurs de directive pour le DSL que vous souhaitez accéder. Cela charge les assemblys pour votre DSL afin que vous puissiez utiliser ses classes de domaine, les propriétés et les relations dans le code de votre modèle de texte. Il charge également le fichier de modèle que vous spécifiez.  
  
 Un `.tt` fichier similaire à l’exemple suivant est créé dans le projet de débogage lorsque vous créez un nouveau [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution à partir du modèle de langage Minimal DSL.  
  
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
  
-   Le modèle peut utiliser les classes de domaine, les propriétés et les relations que vous avez défini dans la définition DSL.  
  
-   Le modèle de charge le fichier de modèle que vous spécifiez dans le `requires` propriété.  
  
-   Une propriété dans `this` contient l’élément racine. À partir de là, votre code peut accéder à d’autres éléments du modèle. Le nom de la propriété est généralement identique à la classe de domaine racine de votre DSL. Dans cet exemple, il s’agit de `this.ExampleModel`.  
  
-   Bien que le langage dans lequel sont écrits les fragments de code c#, vous pouvez générer le texte de tout type. Vous pouvez également écrire le code dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] en ajoutant la propriété `language="VB"` à la `template` directive.  
  
-   Pour déboguer le modèle, vous devez ajouter `debug="true"` à la `template` directive. Le modèle s’ouvre dans une autre instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] si une exception se produit. Si vous souhaitez arrêter le débogueur à un moment précis dans le code, insérez l’instruction `System.Diagnostics.Debugger.Break();`  
  
     Pour plus d’informations, consultez [débogage d’un modèle de texte T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Sur le processeur de directive DSL  
 Le modèle peut utiliser les classes de domaine que vous avez défini dans votre définition DSL. Il est généré par une directive qui apparaît généralement au début du modèle. Dans l’exemple précédent, il est la suivante.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Le nom de la directive ( `MyLanguage`, dans cet exemple) est dérivée du nom de votre DSL. Il appelle un *processeur de directive* qui est généré dans le cadre de votre DSL. Vous pouvez trouver son code source dans **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 Le processeur de directive DSL effectue deux tâches principales :  
  
-   Elle insère efficacement des directives d’assembly et l’importation dans le modèle qui fait référence à votre DSL. Cela vous permet d’utiliser vos classes de domaine dans le code du modèle.  
  
-   Il charge le fichier que vous spécifiez dans le `requires` paramètre et définit une propriété `this` qui fait référence à l’élément racine du modèle chargé.  
  
## <a name="validating-the-model-before-running-the-template"></a>Validation du modèle avant d’exécuter le modèle  
 Vous pouvez provoquer le modèle être validée avant que le modèle est exécuté.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Notez que :  
  
1.  Le `filename` et `validation` paramètres sont séparés par « ; » et il ne doit y avoir aucun autre séparateurs ou espaces.  
  
2.  La liste des catégories de validation détermine les méthodes de validation seront exécutées. Plusieurs catégories doivent être séparées par «&#124;» et il ne doit y avoir aucun autre séparateurs ou espaces.  
  
 Si une erreur se produit, il est signalé dans la fenêtre des erreurs, et le fichier de résultats contiendra un message d’erreur.  
  
##  <a name="Multiple"></a> L’accès à plusieurs modèles à partir d’un modèle de texte  
  
> [!NOTE]
>  Cette méthode vous permet de lire plusieurs modèles dans le même modèle, mais ne prend pas en charge les références ModelBus. Pour lire des modèles qui sont reliées par des références ModelBus, consultez [à l’aide de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Si vous souhaitez accéder à plus d’un modèle à partir du même modèle de texte, vous devez appeler le processeur de directive généré une fois pour chaque modèle. Vous devez spécifier le nom de fichier de chaque modèle dans le `requires` paramètre. Vous devez spécifier les noms que vous souhaitez utiliser pour la classe de domaine racine dans le `provides` paramètre. Vous devez spécifier des valeurs différentes pour le `provides` paramètres dans chacun des appels de directive. Par exemple, supposons que vous disposez de trois fichiers de modèle appelés Library.xyz, School.xyz et Work.xyz. Pour y accéder à partir du même modèle de texte, vous devez écrire trois appels de directive qui ressemblent à celles qui suivent.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Cet exemple de code est d’une langue qui est basée sur le modèle de solution de langage Minimal.  
  
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
  
## <a name="loading-models-dynamically"></a>Chargement dynamique des modèles  
 Si vous souhaitez déterminer, lors de l’exécution, les modèles à charger, vous pouvez charger dynamiquement un fichier de modèle dans votre code de programme, au lieu d’utiliser la directive du DSL spécifique.  
  
 Toutefois, l’une des fonctions de la directive du DSL spécifique consiste à importer l’espace de noms DSL, afin que le code du modèle peut utiliser les classes de domaine définies dans ce DSL. Étant donné que vous n’utilisez pas la directive, vous devez ajouter  **\<assembly >** et  **\<Importer >** directives pour tous les modèles que vous pouvez charger. C’est facile si les différents modèles que vous pouvez charger sont toutes les instances du même DSL.  
  
 Pour charger le fichier, la méthode la plus efficace est à l’aide de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. Dans un scénario classique, votre modèle de texte utilise une directive DSL spécifique pour charger le premier modèle à l’accoutumée. Ce modèle contient les références ModelBus à un autre modèle. Vous pouvez utiliser le ModelBus pour ouvrir le modèle référencé et accéder à un élément particulier. Pour plus d’informations, consultez [à l’aide de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Dans un scénario moins habituel, vous souhaiterez ouvrir un fichier de modèle pour lequel vous avez uniquement un nom de fichier, et qui ne peut pas être en cours [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet. Dans ce cas, vous pouvez ouvrir le fichier à l’aide de la technique décrite dans [Comment : ouvrir un modèle depuis un fichier de Code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Génération de plusieurs fichiers à partir d’un modèle  
 Si vous souhaitez générer plusieurs fichiers – par exemple, pour générer un fichier distinct pour chaque élément dans un modèle, il existe plusieurs approches possibles. Par défaut, un seul fichier est généré à partir de chaque fichier de modèle.  
  
### <a name="splitting-a-long-file"></a>Fractionnement d’un fichier long  
 Dans cette méthode, vous utilisez un modèle pour générer un seul fichier, séparé par un délimiteur. Puis vous fractionnez le fichier en plusieurs parties. Il existe deux modèles, une pour générer le fichier unique et l’autre à fractionner.  
  
 **LoopTemplate.t4** génère le seul fichier long. Notez que son extension de fichier est « .t4 », car il ne doit pas traité directement lorsque vous cliquez sur **transformer tous les modèles**. Ce modèle prend un paramètre, qui spécifie la chaîne de délimiteur qui sépare les segments :  
  
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
  
 `LoopSplitter.tt` appelle `LoopTemplate.t4`et puis fractionne le fichier résultant en ses segments. Notez que ce modèle ne devra pas être un modèle de modélisation, car elle ne lit pas le modèle.  
  
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



