---
title: Génération de code et modèles de texte T4
description: Découvrez comment un modèle de texte T4 est un mélange de blocs de texte et de logique de contrôle qui peut générer un fichier texte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76714be09c38f6426626e94ee7734873c823f704
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389772"
---
# <a name="code-generation-and-t4-text-templates"></a>Génération de code et modèles de texte T4

Dans Visual Studio, un *modèle de texte T4* est un mélange de blocs de texte et de logique de contrôle qui peut générer un fichier texte. La logique de contrôle est écrite comme des fragments de code du programme en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Dans Visual Studio 2015 Update 2 et versions ultérieures, vous pouvez utiliser les fonctionnalités C# version 6.0 dans les directives de modèles T4. Le fichier généré peut être du texte de tout type, tel qu’une page Web ou un fichier de ressources, ou du code source de programme dans n’importe quel langage.

Il existe deux types de modèles de texte T4 : au moment de l’exécution et au moment de la conception.

## <a name="run-time-t4-text-templates"></a>Modèles de texte T4 au moment de l’exécution

Également appelés modèles « prétraités », les modèles au moment de l’exécution sont exécutés dans votre application pour produire des chaînes de texte, généralement dans le cadre de sa sortie. Par exemple, vous pouvez créer un modèle pour définir une page HTML :

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

Votre application peut s’exécuter sur un ordinateur sur lequel Visual Studio n’est pas installé.

Pour créer un modèle au moment de l’exécution, ajoutez un fichier **Modèle de texte prétraité** à votre projet. Vous pouvez également ajouter un fichier texte brut et affecter à sa propriété **Outil personnalisé** la valeur **TextTemplatingFilePreprocessor**.

Pour plus d’informations, consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Pour plus d’informations sur la syntaxe des modèles, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Modèles de texte T4 au moment du design

Les modèles au moment de la conception définissent une partie du code source et d’autres ressources de votre application. En général, vous utilisez plusieurs modèles qui lisent les données dans un fichier ou une base de données d’entrée unique et génèrent des fichiers *. cs*, *. vb* ou d’autres fichiers sources. Chaque modèle génère un fichier. Ils sont exécutés dans Visual Studio ou MSBuild.

Par exemple, vos données d’entrée peuvent être un fichier XML de données de configuration. Chaque fois que vous modifiez le fichier XML pendant le développement, les modèles de texte régénèrent une partie du code de l’application. L’un des modèles peut ressembler à l’exemple suivant :

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

Selon les valeurs du fichier XML, le fichier *. cs* généré ressemble à ce qui suit :

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Autre exemple : l’entrée peut être un diagramme de flux de travail dans une activité d’entreprise. Quand les utilisateurs modifient leur flux de travail d’entreprise ou que vous commencez à travailler avec de nouveaux utilisateurs qui ont un flux de travail différent, il est facile de régénérer le code pour l’adapter au nouveau modèle.

Les modèles au moment du design rendent la modification de la configuration plus rapide et plus fiable quand les spécifications changent. En général, l’entrée est définie en termes de besoins de l’entreprise, comme dans l’exemple de flux de travail. Cela facilite les discussions avec vos utilisateurs concernant les changements. Par conséquent, les modèles au moment du design sont un outil utile dans un processus de développement agile.

Pour créer un modèle au moment du design, ajoutez un fichier **Modèle de texte** à votre projet. Vous pouvez également ajouter un fichier texte brut et affecter à sa propriété **Outil personnalisé** la valeur **TextTemplatingFileGenerator**.

Pour plus d’informations, consultez [génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Pour plus d’informations sur la syntaxe des modèles, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Le terme *modèle* est parfois utilisé pour décrire les données lues par un ou plusieurs modèles. Le modèle peut se présenter sous n’importe quel format, dans tout type de fichier ou de base de données. Il n’est pas tenu d’être un modèle UML ni un modèle de langage spécifique à un domaine. Le terme « modèle » indique seulement que les données peuvent être définies en termes de concepts d’entreprise, plutôt que de ressembler au code.

La fonctionnalité de transformation de modèle de texte est appelée *T4*.

## <a name="see-also"></a>Voir aussi

- [Générer du code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)
