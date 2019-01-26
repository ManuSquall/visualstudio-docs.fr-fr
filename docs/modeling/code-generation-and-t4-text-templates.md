---
title: Génération de code et modèles de texte T4
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c3f4e654c5bcaf373d8358201c856cc8667043d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034475"
---
# <a name="code-generation-and-t4-text-templates"></a>Génération de code et modèles de texte T4

Dans Visual Studio, un *modèle de texte T4* est un mélange de blocs de texte et la logique de contrôle qui peut générer un fichier texte. La logique de contrôle est écrite comme des fragments de code du programme en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Dans Visual Studio 2015 Update 2 et versions ultérieures, vous pouvez utiliser les fonctionnalités C# version 6.0 dans les directives de modèles T4. Le fichier généré peut être du texte de tout type, comme une page web, ou d’un fichier de ressources ou d’un code source de programme dans n’importe quel langage.

Il existe deux types de modèles de texte T4 : temps d’exécution et moment du design.

## <a name="run-time-t4-text-templates"></a>Modèles de texte T4 exécution

Également connu sous les modèles « prétraités », modèles d’exécution sont exécutées dans votre application pour produire des chaînes de texte, généralement dans le cadre de sa sortie. Par exemple, vous pouvez créer un modèle pour définir une page HTML :

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Remarquez que le modèle ressemble à la sortie générée. La ressemblance du modèle avec la sortie obtenue vous aide à éviter des erreurs quand vous voulez le modifier.

De plus, le modèle contient des fragments de code du programme. Vous pouvez utiliser ces fragments pour répéter des sections de texte, organiser des sections conditionnelles et afficher des données de votre application.

Pour générer la sortie, votre application appelle une fonction générée par le modèle. Exemple :

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Votre application peut s’exécuter sur un ordinateur qui n’a pas installé Visual Studio.

Pour créer un modèle au moment de l’exécution, ajoutez un fichier **Modèle de texte prétraité** à votre projet. Vous pouvez également ajouter un fichier texte brut et affecter à sa propriété **Outil personnalisé** la valeur **TextTemplatingFilePreprocessor**.

Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Pour plus d’informations sur la syntaxe des modèles, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Concevoir des modèles de texte T4 de temps

Modèles de temps de conception définissent une partie du code source et autres ressources de votre application. En général, vous utilisez plusieurs modèles qui lisent les données dans un seul fichier d’entrée ou de la base de données et générer certaines de vos *.cs*, *.vb*, ou d’autres fichiers sources. Chaque modèle génère un fichier. Ils sont exécutés dans Visual Studio ou MSBuild.

Par exemple, vos données d’entrée peuvent être un fichier XML de données de configuration. Chaque fois que vous modifiez le fichier XML pendant le développement, les modèles de texte régénérer la partie du code d’application. L’un des modèles peut ressembler à l’exemple suivant :

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

En fonction des valeurs dans le fichier XML, généré *.cs* fichier se présente comme suit :

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Autre exemple : l’entrée peut être un diagramme de flux de travail dans une activité d’entreprise. Quand les utilisateurs modifient leur flux de travail d’entreprise ou que vous commencez à travailler avec de nouveaux utilisateurs qui ont un flux de travail différent, il est facile de régénérer le code pour l’adapter au nouveau modèle.

Les modèles au moment du design rendent la modification de la configuration plus rapide et plus fiable quand les spécifications changent. En général, l’entrée est définie en termes de besoins de l’entreprise, comme dans l’exemple de flux de travail. Cela facilite les discussions avec vos utilisateurs concernant les changements. Par conséquent, les modèles au moment du design sont un outil utile dans un processus de développement agile.

Pour créer un modèle au moment du design, ajoutez un fichier **Modèle de texte** à votre projet. Vous pouvez également ajouter un fichier texte brut et affecter à sa propriété **Outil personnalisé** la valeur **TextTemplatingFileGenerator**.

Pour plus d’informations, consultez [génération de Code au moment du Design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Pour plus d’informations sur la syntaxe des modèles, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Le terme *modèle* est parfois utilisé pour décrire les données lues par un ou plusieurs modèles. Le modèle peut se présenter sous n’importe quel format, dans tout type de fichier ou de base de données. Il n’est pas tenu d’être un modèle UML ni un modèle de langage spécifique à un domaine. Le terme « modèle » indique seulement que les données peuvent être définies en termes de concepts d’entreprise, plutôt que de ressembler au code.

La fonctionnalité de transformation de modèle de texte est appelée *T4*.

## <a name="see-also"></a>Voir aussi

- [Générer du code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)
