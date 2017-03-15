---
title: "T4 Parameter Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 Parameter Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans un modèle de texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directive `parameter` déclare des propriétés dans votre code du modèle, qui sont initialisées à partir de valeurs passées par le contexte externe.  Vous pouvez définir ces valeurs si vous écrivez du code qui appelle la transformation de texte.  
  
## Utilisation de la directive du paramètre  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 La directive `parameter` déclare des propriétés dans votre code du modèle, qui sont initialisées à partir de valeurs passées par le contexte externe.  Vous pouvez définir ces valeurs si vous écrivez du code qui appelle la transformation de texte.  Les valeurs peuvent être passées dans le dictionnaire `Session` ou dans <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Vous pouvez déclarer les paramètres de tout type accessible à distance.  Autrement dit, le type doit être déclaré avec <xref:System.SerializableAttribute>, ou il doit dériver de <xref:System.MarshalByRefObject>.  Cela permet le passage des valeurs de paramètre dans l'AppDomain dans lequel le modèle est traité.  
  
 Par exemple, vous pouvez écrire un modèle de texte avec le contenu suivant :  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## Passage de valeurs de paramètre à un modèle  
 Si vous écrivez une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] telle qu'une commande de menu ou un gestionnaire d'événements, vous pouvez traiter un modèle à l'aide du service de création de modèles de texte :  
  
```c#  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## Passage de valeurs dans le contexte d'appel  
 Vous pouvez également passer des valeurs en tant que données logiques dans <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 L'exemple suivant passe des valeurs à l'aide de deux méthodes :  
  
```c#  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## Passage de valeurs à un modèle de texte au moment de l'exécution \(prétraité\)  
 En général, il n'est pas nécessaire d'utiliser la directive `<#@parameter#>` avec les modèles de texte au moment de l'exécution \(prétraités\).  À la place, vous pouvez définir un constructeur supplémentaire ou une propriété définissable pour le code généré, que vous utilisez pour passer des valeurs de paramètre.  Pour plus d'informations, consultez [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Toutefois, si vous souhaitez utiliser `<#@parameter>` dans un modèle au moment de l'exécution, vous pouvez lui passer des valeurs à l'aide du dictionnaire de session.  Par exemple, supposons que vous avez créé le fichier comme un modèle prétraité appelé `PreTextTemplate1`.  Vous pouvez appeler le modèle dans votre programme à l'aide du code suivant.  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## Obtention d'arguments de TextTemplate.exe  
  
> [!IMPORTANT]
>  La directive `parameter` n'extrait pas les valeurs définies dans le paramètre `–a` de l'utilitaire `TextTransform.exe`.  Pour obtenir ces valeurs, définissez `hostSpecific="true"` dans la directive `template` et utilisez `this.Host.ResolveParameterValue("","","argName")`.