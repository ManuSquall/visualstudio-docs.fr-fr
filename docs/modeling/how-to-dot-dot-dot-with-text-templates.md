---
title: 'Comment : écrire avec des modèles de texte'
description: Découvrez les réponses aux questions courantes rencontrées lors de l’utilisation de modèles de texte pour générer du texte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c65a7ba67c3972620b3d589188e233827a12ffd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387266"
---
# <a name="how-to--with-text-templates"></a>Comment : écrire avec des modèles de texte
Les modèles de texte dans Visual Studio fournissent un moyen utile de générer du texte de n’importe quel type. Vous pouvez utiliser des modèles de texte pour générer du texte au moment de l’exécution dans le cadre de votre application et au moment de la conception pour générer une partie du code de votre projet. Cette rubrique résume les « Comment faire... ? » les plus fréquemment posées. poser.

 Dans cette rubrique, plusieurs réponses précédées de puces sont des suggestions alternatives.

 Pour obtenir une présentation générale des modèles de texte, consultez [génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Comment...

### <a name="generate-part-of-my-application-code"></a>Générer une partie de mon code d’application
 Je dispose d’une configuration ou d’un *modèle* dans un fichier ou une base de données. Une ou plusieurs parties de mon code dépendent de ce modèle.

- Générez certains de vos fichiers de code à partir de modèles de texte. Pour plus d’informations, consultez [génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) et [quelle est la meilleure façon de commencer à écrire un modèle ?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Générer des fichiers au moment de l’exécution, en passant des données dans le modèle
 Au moment de l’exécution, mon application génère des fichiers texte, tels que des rapports, qui contiennent un mélange de texte et de données standard. Je souhaite éviter d’écrire des centaines d' `write` instructions.

- Ajoutez un modèle de texte au moment de l’exécution à votre projet. Ce modèle crée une classe dans votre code, que vous pouvez instancier et utiliser pour générer du texte. Vous pouvez lui passer des données dans les paramètres du constructeur. Pour plus d’informations, consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Si vous souhaitez générer à partir de modèles qui sont uniquement disponibles au moment de l’exécution, vous pouvez utiliser des modèles de texte standard. Si vous écrivez une extension Visual Studio, vous pouvez appeler le service de création de modèles de texte. Pour plus d’informations, consultez [appel de la transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md). Dans d’autres contextes, vous pouvez utiliser le moteur de création de modèles de texte. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Utilisez la \<#@parameter#> directive pour passer des paramètres à ces modèles. Pour plus d’informations, consultez [directive de paramètre T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Lire un autre fichier projet à partir d’un modèle
 Pour lire un fichier à partir du même projet Visual Studio que le modèle :

- Insérez `hostSpecific="true"` dans la directive `<#@template#>`.

     Dans votre code, utilisez `this.Host.ResolvePath(filename)` pour obtenir le chemin d’accès complet du fichier.

### <a name="invoke-methods-from-a-template"></a>Appeler des méthodes à partir d’un modèle

Si les méthodes existent déjà, par exemple dans les classes .NET :

- Utilisez la \<#@assembly#> directive pour charger l’assembly et utilisez \<#@import#> pour définir le contexte de l’espace de noms. Pour plus d’informations, consultez [directive import T4](../modeling/t4-import-directive.md).

   Si vous utilisez fréquemment le même jeu de directives d’assembly et d’importation, envisagez d’écrire un processeur de directive. Dans chaque modèle, vous pouvez appeler le processeur de directive, qui peut charger les assemblys et les fichiers de modèle et définir le contexte de l’espace de noms. Pour plus d’informations, consultez [création de processeurs de directive de modèle de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md).

Si vous écrivez les méthodes vous-même :

- Si vous écrivez un modèle de texte Runtime, écrivez une définition de classe partielle qui porte le même nom que votre modèle de texte d’exécution. Ajoutez les méthodes supplémentaires à cette classe.

- Écrivez un bloc `<#+ ... #>` de contrôle de fonctionnalité de classe dans lequel vous pouvez déclarer des méthodes, des propriétés et des classes privées. Lorsque le modèle de texte est compilé, il est transformé en classe. Les blocs de contrôle standard `<#...#>` et le texte sont transformés en une méthode unique, et les blocs de fonctionnalité de classe sont insérés en tant que membres distincts. Pour plus d’informations, consultez [blocs de contrôle de modèle de texte](../modeling/text-template-control-blocks.md).

   Les méthodes définies en tant que fonctionnalités de classe peuvent également inclure des blocs de texte incorporés.

   Envisagez de placer des fonctionnalités de classe dans un fichier distinct, que vous pouvez utiliser dans `<#@include#>` un ou plusieurs fichiers modèles.

- Écrivez les méthodes dans un assembly séparé (bibliothèque de classes) et appelez-les à partir de votre modèle. Utilisez la `<#@assembly#>` directive pour charger l’assembly et `<#@import#>` définir le contexte de l’espace de noms. Notez que pour régénérer l’assembly pendant que vous le déboguez, vous devrez peut-être arrêter et redémarrer Visual Studio. Pour plus d’informations, consultez Directives pour les [modèles de texte T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Générer de nombreux fichiers à partir d’un schéma de modèle
 Si vous générez souvent des fichiers à partir de modèles qui ont le même schéma de base de données ou XML :

- Envisagez d’écrire un processeur de directive. Cela vous permet de remplacer plusieurs instructions d’assembly et d’importer dans chaque modèle par une directive personnalisée unique. Le processeur de directive peut également charger et analyser le fichier de modèle. Pour plus d’informations, consultez [création de processeurs de directive de modèle de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Générer des fichiers à partir d’un modèle complexe

- Envisagez de créer un langage spécifique à un domaine (DSL) pour représenter le modèle. Il est ainsi beaucoup plus facile d’écrire les modèles, car vous utilisez des types et des propriétés qui reflètent les noms des éléments dans votre modèle. Vous n’avez pas besoin d’analyser le fichier ou de naviguer dans les nœuds XML. Exemple :

     `foreach (Book book in this.Library) { ... }`

     Pour plus d’informations, consultez [prise en main avec les langages de Domain-Specific](../modeling/getting-started-with-domain-specific-languages.md) et [génération de code à partir d’un langage de Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Récupérer des données à partir de Visual Studio
 Pour utiliser les services fournis dans Visual Studio, définissez l' `hostSpecific` attribut et chargez l' `EnvDTE` assembly. Exemple :

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Exécuter des modèles de texte dans le processus de génération

- Pour plus d’informations, consultez [génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Questions générales

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Quelle est la meilleure façon de commencer à écrire un modèle de texte ?

1. Écrivez un exemple spécifique du fichier généré.

2. Transformez-le en un modèle de texte en insérant la `<#@template #>` directive, ainsi que les directives et le code requis pour charger le fichier ou le modèle d’entrée.

3. Remplacez progressivement des parties du fichier par des blocs d’expression et de code.

### <a name="what-is-a-model"></a>Qu’est un « modèle » ?

- Entrée lue par votre modèle. Il peut se trouver dans un fichier ou dans une base de données. Il peut s’agir d’un fichier XML, d’un dessin Visio, d’un langage spécifique à un domaine (DSL) ou d’un modèle UML, ou de texte brut. Il peut être réparti sur plusieurs fichiers. En général, plusieurs modèles lisent un modèle.

     L’implication du terme « modèle » est qu’il représente un aspect de votre entreprise plus directement que le code du programme généré ou d’autres fichiers. Par exemple, il peut représenter le plan d’un réseau de communication que vos logiciels générés doivent superviser.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Quel est l’avantage de l’utilisation des modèles de texte ?
 En général, vous générez plusieurs fichiers de code ou d’autres fichiers à partir d’un modèle. Le modèle représente les spécifications plus directement que le code généré. Il omet les détails de l’implémentation et est écrit en termes de spécifications, plutôt que dans le code. Lorsque les spécifications changent, comme elles le font habituellement, vous pouvez mettre à jour le modèle plus facilement et de manière plus fiable que les différentes parties du code du programme.

 La génération de code est donc un outil précieux du point de vue des méthodes de développement Agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Quelles sont les « meilleures pratiques » pour les modèles de texte ?

- Pour plus d’informations, consultez [instructions pour l’écriture de modèles de texte T4](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Qu’est-ce que « T4 » ?

- Un autre nom pour les fonctionnalités du modèle de texte Visual Studio décrit ici. La version précédente, qui n’a pas été publiée, était une abréviation pour « transformation de modèle de texte ».
