---
title: "Génération de code et modèles de texte T4 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6eeadb77cd0250ab7b2cc48c2abdb8d9f1a1f373
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="code-generation-and-t4-text-templates"></a>Génération de code et modèles de texte T4
Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], un *modèle de texte T4* est un mélange de blocs de texte et de logique de contrôle qui peut générer un fichier texte. La logique de contrôle est écrite comme des fragments de code du programme en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Dans Visual Studio 2015 Update 2 et versions ultérieures, vous pouvez utiliser les fonctionnalités C# version 6.0 dans les directives de modèles T4. Le fichier généré peut être du texte de tout type, tel qu’une page web ou un fichier de ressources, ou du code source de programme dans tout langage.  
  
 Il existe deux types de modèles de texte T4 :  
  
 Les**modèles de texte T4 d’exécution** (modèles « prétraités ») sont exécutés dans votre application pour produire des chaînes de texte, généralement dans le cadre de sa sortie.  
 Par exemple, vous pouvez créer un modèle pour définir une page HTML :  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 Remarquez que le modèle ressemble à la sortie générée. La ressemblance du modèle avec la sortie obtenue vous aide à éviter des erreurs quand vous voulez le modifier.  
  
 De plus, le modèle contient des fragments de code du programme. Vous pouvez utiliser ces fragments pour répéter des sections de texte, organiser des sections conditionnelles et afficher des données de votre application.  
  
 Pour générer la sortie, votre application appelle une fonction générée par le modèle. Exemple :  
  
```csharp  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 Votre application peut s’exécuter sur un ordinateur sur lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n’est pas installé.  
  
 Pour créer un modèle au moment de l’exécution, ajoutez un fichier **Modèle de texte prétraité** à votre projet. Vous pouvez également ajouter un fichier texte brut et affecter à sa propriété **Outil personnalisé** la valeur **TextTemplatingFilePreprocessor**.  
  
 Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Pour plus d’informations sur la syntaxe des modèles, consultez [l’écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).  
  
 Les**modèles de texte T4 au moment du design** sont exécutés dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour définir une partie du code source et d’autres ressources de votre application.  
 En général, vous utilisez plusieurs modèles qui lisent les données dans une base de données ou un fichier d’entrée unique et génèrent une partie de vos fichiers `.cs`ou `.vb`, ou d’autres fichiers sources. Chaque modèle génère un fichier. Ils sont exécutés dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Par exemple, vos données d’entrée peuvent être un fichier XML de données de configuration. Chaque fois que vous modifiez le fichier XML pendant le développement, les modèles de texte régénèrent une partie du code d’application. L’un des modèles peut ressembler à l’exemple suivant :  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 En fonction des valeurs dans le fichier XML, le fichier `.cs` généré peut ressembler à ce qui suit :  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 Autre exemple : l’entrée peut être un diagramme de flux de travail dans une activité d’entreprise. Quand les utilisateurs modifient leur flux de travail d’entreprise ou que vous commencez à travailler avec de nouveaux utilisateurs qui ont un flux de travail différent, il est facile de régénérer le code pour l’adapter au nouveau modèle.  
  
 Les modèles au moment du design rendent la modification de la configuration plus rapide et plus fiable quand les spécifications changent. En général, l’entrée est définie en termes de besoins de l’entreprise, comme dans l’exemple de flux de travail. Cela facilite les discussions avec vos utilisateurs concernant les changements. Par conséquent, les modèles au moment du design sont un outil utile dans un processus de développement agile.  
  
 Pour créer un modèle au moment du design, ajoutez un fichier **Modèle de texte** à votre projet. Vous pouvez également ajouter un fichier texte brut et affecter à sa propriété **Outil personnalisé** la valeur **TextTemplatingFileGenerator**.  
  
 Pour plus d’informations, consultez [génération du Code à l’aide de modèles de texte T4 au moment du Design](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Pour plus d’informations sur la syntaxe des modèles, consultez [l’écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Le terme *modèle* est parfois utilisé pour décrire les données lues par un ou plusieurs modèles. Le modèle peut se présenter sous n’importe quel format, dans tout type de fichier ou de base de données. Il n’est pas tenu d’être un modèle UML ni un modèle de langage spécifique à un domaine. Le terme « modèle » indique seulement que les données peuvent être définies en termes de concepts d’entreprise, plutôt que de ressembler au code.  
  
 La fonctionnalité de transformation de modèle de texte est appelée *T4*.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Génération de texte à l’exécution à l’aide des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 Dans toute application qui génère des fichiers texte, les modèles de texte précompilés constituent une méthode simple et fiable pour définir le texte. Toutefois, cette méthode ne peut pas être utilisée pour les modèles de texte qui changent au moment de l’exécution.  
  
 [Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 La génération de code et d’autres ressources à partir d’un modèle vous permet de mettre à jour votre application en mettant à jour le modèle.  
  
 [Génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md)  
 Si vous avez installé le Kit de développement logiciel (SDK) Visualization and Modeling pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , vous pouvez garantir que le logiciel généré restera à jour des modifications dans le modèle.  
  
 [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)  
 Syntaxe d’un fichier modèle de texte.  
  
 [Procédure pas à pas : génération de code à l’aide de modèles de texte](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Démonstration d’une façon d’utiliser la génération de code.  
  
 [Débogage d’un modèle de texte T4](../modeling/debugging-a-t4-text-template.md)  
 Comment déboguer des modèles de texte et résoudre certaines erreurs courantes liées aux modèles de texte.  
  
 [Génération de fichiers avec l’utilitaire TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)  
 Outil en ligne de commande qui permet d’exécuter des transformations du modèle de texte.  
  
 [Personnalisation d’une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)  
 Comment écrire des processeurs de directive et des hôtes de modèles personnalisés pour vos propres sources de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)