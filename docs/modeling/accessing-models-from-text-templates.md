---
title: "Acc&#232;s aux mod&#232;les depuis des mod&#232;les de texte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles de texte, accéder aux modèles"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# Acc&#232;s aux mod&#232;les depuis des mod&#232;les de texte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En utilisant des modèles de texte, vous pouvez créer des fichiers de rapports, les fichiers de code source, et d'autres fichiers texte sont basés sur des modèles de langage spécifique à un domaine.  Pour des informations de base sur les modèles de texte, consultez [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md).  Les modèles de texte s'exécutent en mode expérimental lorsque vous déboguez votre DÉSOLÉ, et utilisés également sur un ordinateur sur lequel vous avez déployé le langage spécifique à un domaine.  
  
> [!NOTE]
>  Lorsque vous créez une solution DÉSOLÉ, les fichiers d' **\*.tt** de modèle de texte exemple sont générés dans le projet de débogage.  Lorsque vous modifiez les classes de noms du domaine, ces modèles ne fonctionneront plus.  Néanmoins, ils comprennent des directives de base dont vous avez besoin, et fournissent des exemples que vous pouvez mettre à jour pour correspondre à votre DÉSOLÉ.  
  
 pour accéder à un modèle d'un modèle de texte :  
  
-   Affectez à la propriété hériter de la directive de modèle à <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>.  Cela permet d'accéder au magasin.  
  
-   Spécifiez les processeurs de directive pour le langage spécifique à un domaine auquel vous souhaitez accéder.  Cette opération permet de charger les assemblys de votre DÉSOLÉ afin que vous puissiez utiliser ses classes, propriétés, et relations de domaine dans le code de votre modèle de texte.  il charge également le fichier de modèle que vous spécifiez.  
  
 Un fichier d' `.tt` similaire à l'exemple suivant est créé dans le projet de débogage lorsque vous créez une solution de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] du modèle minimal de langage DÉSOLÉ.  
  
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
  
 Notez les points suivants à propos de ce modèle :  
  
-   Le modèle peut utiliser les classes, propriétés, et les relations que vous avez définies dans la définition de langage spécifique à un domaine.  
  
-   le modèle charge le fichier de modèle que vous spécifiez dans la propriété d' `requires` .  
  
-   une propriété dans `this` contient l'élément racine.  De là, votre code peut accéder à d'autres éléments du modèle.  Le nom de la propriété est habituellement similaire à la classe de domaine racine de votre DÉSOLÉ.  Dans cet exemple, il est `this.ExampleModel`.  
  
-   Bien que le langage dans lequel les fragments de code sont écrits soit c\#, vous pouvez générer du texte de tout type.  Vous pouvez également écrire du code dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en ajoutant la propriété `language="VB"` à la directive d' `template` .  
  
-   pour déboguer le modèle, ajoutez `debug="true"` à la directive d' `template` .  Le modèle s'ouvre dans une autre instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si une exception se produit.  Si vous souhaitez arrêter le débogueur à un point spécifique dans le code, insérez l'instruction `System.Diagnostics.Debugger.Break();`  
  
     Pour plus d'informations, consultez [Debugging a T4 Text Template](../modeling/debugging-a-t4-text-template.md).  
  
## Sur le processeur de directive DÉSOLÉ  
 Le modèle peut utiliser les classes de domaine que vous avez défini dans votre définition de langage spécifique à un domaine.  Cette erreur est provoquée par une directive qui apparaît généralement vers le début du modèle.  dans l'exemple précédent, il est le suivant.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Le nom de la directive \( `MyLanguage`, dans cet exemple\) est dérivé du nom de votre DÉSOLÉ.  Il appelle *un processeur de directive* qui est généré dans le cadre de votre DÉSOLÉ.  vous pouvez rechercher son code source dans **Dsl\\GeneratedCode\\DirectiveProcessor.cs**.  
  
 Le processeur de directive DÉSOLÉ exécute deux tâches principales :  
  
-   Il insère efficacement des directives d'assembly et d'importer dans le modèle qui référence votre DÉSOLÉ.  Cela vous permet d'utiliser vos classes de domaine dans le code du modèle.  
  
-   Il charge le fichier spécifié dans le paramètre d' `requires` , et définit une propriété dans `this` qui fait référence à l'élément racine du modèle chargé.  
  
## Valider le modèle avant d'exécuter le modèle  
 Vous pouvez provoquer un modèle à valider avant que le modèle soit exécuté.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Notez que :  
  
1.  Les paramètres d' `filename` et d' `validation` sont séparés par « ;  » et il ne doit y avoir d'autre séparateur ou espace.  
  
2.  La liste des catégories de validation détermine les méthodes de validation sont exécuté.  Plusieurs catégories doivent être séparées par « &#124; » et il ne doit y avoir d'autre séparateur ou espace.  
  
 Si une erreur est détectée, il est stocké dans la fenêtre d'erreur, et le fichier de résultats contiendra un message d'erreur.  
  
##  <a name="Multiple"></a> plusieurs modèles de accès d'un modèle de texte  
  
> [!NOTE]
>  Cette méthode vous permet de lire plusieurs modèles dans le même modèle mais ne prend pas en charge les références ModelBus.  Pour lire des modèles qui sont liés par des références de ModelBus, consultez l' [Utilisation de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Si vous souhaitez accéder à plusieurs modèle du même modèle de texte, vous devez appeler le processeur de directive généré une fois pour chaque modèle.  vous devez spécifier le nom de fichier de chaque modèle dans le paramètre d' `requires` .  vous devez spécifier les noms que vous souhaitez utiliser pour la classe de domaine racine dans le paramètre d' `provides` .  Vous devez spécifier des valeurs pour les paramètres d' `provides` dans chacun des appels de directives.  par exemple, supposez que vous avez trois fichiers de modèle appelés Library.xyz, School.xyz, et Work.xyz.  Pour y accéder à partir de le modèle de texte, vous devez écrire trois appels de directives qui ressemblent les suivants.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Cet exemple de code est pour un langage basé sur le modèle minimal de solution de langage.  
  
 Pour accéder aux modèles dans votre modèle de texte, vous pouvez maintenant écrire le code semblable au code dans l'exemple suivant.  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## Le chargement modèle dynamique  
 Si vous voulez déterminer au moment de l'exécution qui modélise à charger, vous pouvez charger un fichier modèle dynamiquement dans votre code de programme, au lieu d'utiliser la directive de DSL\-détail.  
  
 Toutefois, l'une des fonctions de la directive de DSL\-détail est d'importer l'espace de noms DÉSOLÉ, afin que le code du modèle puisse utiliser les classes de domaine définies dans ce langage spécifique à un domaine.  Comme vous n'utilisez pas la directive, vous devez ajouter **\<assembly\>** les directives et d' **\<import\>** pour tous les modèles que vous pouvez charger.  C'est facile si les différents modèles que vous pouvez charger sont toutes les instances du même DÉSOLÉ.  
  
 Pour charger le fichier, la méthode la plus efficace consiste à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus.  Dans un scénario classique, votre modèle de texte utilise une directive de DSL\-détail pour charger le premier modèle comme d'habitude.  Que le modèle contient des références ModelBus à un autre modèle.  Vous pouvez utiliser ModelBus pour ouvrir le modèle référencé et pour accéder à un élément particulier.  Pour plus d'informations, consultez [Utilisation de Visual Studio ModelBus dans un modèle de texte](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Dans un scénario moins souvent, vous souhaitiez ouvrir un fichier modèle pour lequel vous avez un seul nom de fichier, et lequel ne peut pas être dans le projet actuel de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Dans ce cas, vous pouvez ouvrir le fichier en utilisant la technique décrite dans [Comment : ouvrir un modèle depuis un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## Générant plusieurs fichiers à partir d'un modèle  
 Si vous souhaitez générer plusieurs fichiers \(par exemple, pour générer un fichier séparé pour chaque élément de modèle, il existe plusieurs approches possibles.  Par défaut, un seul fichier est produit à partir de chaque fichier modèle.  
  
### fractionner un long fichier  
 Dans cette méthode, vous utilisez un modèle pour générer un fichier unique, séparés par un séparateur.  Vous fractionné le fichier en ses parties.  Il existe deux modèles, un pour générer le fichier unique, et l'autre pour le fractionnement.  
  
 **LoopTemplate.t4** génère le long fichier unique.  Notez que son extension de fichier est « .t4 », car elle ne doit pas être traitée directement lorsque vous cliquez sur **Transformer tous les modèles**.  ce modèle prend un paramètre, qui spécifie la chaîne de délimiteur qui sépare les segments :  
  
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
  
 `LoopSplitter.tt` appelle `LoopTemplate.t4`, puis coupez le fichier résultant en ses segments.  Remarquez que ce modèle ne doit pas être un modèle de modélisation, car il ne lit pas le modèle.  
  
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