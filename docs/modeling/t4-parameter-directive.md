---
title: "T4 Directive du paramètre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 468c4716038e3f082435984ff74c7369c200d9db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="t4-parameter-directive"></a>Directive du paramètre T4
Dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de texte, la `parameter` directive déclare des propriétés dans votre code de modèle qui sont initialisées à partir de valeurs passées par le contexte externe. Vous pouvez définir ces valeurs si vous écrivez du code qui appelle la transformation de texte.  
  
## <a name="using-the-parameter-directive"></a>À l’aide de la Directive du paramètre  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 Le `parameter` directive déclare des propriétés dans votre code de modèle qui sont initialisées à partir de valeurs passées par le contexte externe. Vous pouvez définir ces valeurs si vous écrivez du code qui appelle la transformation de texte. Les valeurs peuvent être passées dans le `Session` dictionnaire, ou dans <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Vous pouvez déclarer des paramètres de n’importe quel type accessible à distance. Autrement dit, le type doit être déclaré avec <xref:System.SerializableAttribute>, ou il doit dériver de <xref:System.MarshalByRefObject>. Ainsi, les valeurs de paramètre à passer dans l’AppDomain dans lequel le modèle est traité.  
  
 Par exemple, vous pouvez écrire un modèle de texte avec le contenu suivant :  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Passer des valeurs de paramètre à un modèle  
 Si vous écrivez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension comme une commande de menu ou un gestionnaire d’événements, vous pouvez traiter un modèle à l’aide du service de création de modèles de texte :  
  
```csharp  
// Get a service provider - how you do this depends on the context:  
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
  
## <a name="passing-values-in-the-call-context"></a>Passage de valeurs dans le contexte d’appel  
 Vous pouvez également passer des valeurs comme l’opérateur logique des données dans <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 L’exemple suivant passe des valeurs à l’aide de ces deux méthodes :  
  
```csharp  
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
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passer des valeurs à un modèle de texte d’exécution (prétraité)  
 Il est généralement pas nécessaire d’utiliser la `<#@parameter#>` directive avec les modèles de texte au moment de l’exécution (prétraité). Au lieu de cela, vous pouvez définir un constructeur supplémentaire ou une propriété définissable pour le code généré, par le biais duquel vous passez des valeurs de paramètre. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Toutefois, si vous souhaitez utiliser `<#@parameter>` dans un modèle au moment de l’exécution, vous pouvez passer des valeurs à celui-ci à l’aide du dictionnaire de Session. Par exemple, supposons que vous avez créé le fichier comme un modèle prétraité appelé `PreTextTemplate1`. Vous pouvez appeler le modèle dans votre programme en utilisant le code suivant.  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Obtention d’arguments de TextTemplate.exe  
  
> [!IMPORTANT]
>  Le `parameter` directive ne récupère pas les valeurs définies dans le `-a` paramètre de la `TextTransform.exe` utilitaire. Pour obtenir ces valeurs, définissez `hostSpecific="true"` dans les `template` directive et utilisez `this.Host.ResolveParameterValue("","","argName")`.