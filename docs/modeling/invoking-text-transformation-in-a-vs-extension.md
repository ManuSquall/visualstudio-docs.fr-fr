---
title: Appel d’une transformation de texte dans une extension VS
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f6c325e4ab99413e04cc35bd05babbe6a3dd0c1e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002321"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Appel d’une transformation de texte dans une extension VS
Si vous écrivez une extension de Visual Studio comme une commande de menu ou [langage spécifique à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), vous pouvez utiliser le service de création de modèles de texte pour transformer les modèles de texte. Obtenez le service <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> et effectuez le cast de celui-ci en <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.

## <a name="getting-the-text-templating-service"></a>Obtention du service de création de modèles de texte

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="passing-parameters-to-the-template"></a>Transmission des paramètres au modèle
 Vous pouvez passer des paramètres dans le modèle. À l'intérieur du modèle, vous pouvez obtenir les valeurs de paramètre à l'aide de la directive `<#@parameter#>`.

 Pour le type d'un paramètre, vous devez utiliser un type qui est sérialisable ou qui peut être marshalé. Autrement dit, le type doit être déclaré avec <xref:System.SerializableAttribute>, ou il doit être dérivé de <xref:System.MarshalByRefObject>. Cette restriction est nécessaire car le modèle de texte est exécuté dans un AppDomain séparé. Tous les types intégrés tels que **System.String** et **System.Int32** sont sérialisables.

 Pour passer des valeurs de paramètre, le code appelant peut placer des valeurs dans le dictionnaire `Session` ou dans le <xref:System.Runtime.Remoting.Messaging.CallContext>.

 L'exemple suivant utilise les deux méthodes pour transformer un modèle de test court :

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>Rapport d'erreurs et directive de sortie
 Toutes les erreurs qui surviennent pendant le traitement seront affichera dans la fenêtre d’erreurs Visual Studio. De plus, vous pouvez être informé des erreurs en spécifiant un rappel qui implémente <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.

 Si vous souhaitez écrire la chaîne de résultat dans un fichier, vous souhaitez peut-être connaître l'extension de fichier et l'encodage spécifiés dans la directive `<#@output#>` dans le modèle. Ces informations seront également passées à votre rappel. Pour plus d’informations, consultez [Directive de sortie T4](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

 Le code peut être testé avec un fichier modèle semblable au suivant :

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

 L’avertissement du compilateur apparaîtront dans la fenêtre d’erreur de Visual Studio, et il génère également un appel à `ErrorCallback`.

## <a name="reference-parameters"></a>Paramètres de référence
 Vous pouvez passer des valeurs en dehors d'un modèle de texte à l'aide d'une classe de paramètre dérivée de <xref:System.MarshalByRefObject>.

## <a name="related-topics"></a>Rubriques connexes
 Pour générer du texte à partir d'un modèle de texte prétraité : Appelez la méthode `TransformText()` de la classe générée. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Pour générer du texte en dehors d’une extension Visual Studio : Définissez un hôte personnalisé. Pour plus d’informations, consultez [de traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Pour générer du code source qui peut ensuite être compilé et exécuté : Appelez la méthode `t4.PreprocessTemplate()` de <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.
