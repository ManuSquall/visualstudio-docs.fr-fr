---
title: 'Comment : écrire avec des modèles de texte'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 668ef447673897ce02d5d988ce20839006fead09
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="how-to--with-text-templates"></a>Comment : écrire avec des modèles de texte
Modèles de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offrent un moyen utile de générer du texte de n’importe quel type. Vous pouvez utiliser des modèles de texte pour générer du texte au moment de l’exécution en tant que partie de votre application et au moment du design pour générer une partie de votre code de projet. Cette rubrique résume les plus fréquemment posées « Comment... ? » questions.

 Dans cette rubrique, les réponses multiples qui sont précédés de puces sont des suggestions alternatives.

 Pour obtenir une introduction générale aux modèles de texte, consultez [génération de Code et les modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Comment...

### <a name="generate-part-of-my-application-code"></a>Générer une partie du code de mon application
 Disposez d’une configuration ou *modèle* dans un fichier ou une base de données. Une ou plusieurs parties de mon code dépendent de ce modèle.

-   Génèrent une partie de vos fichiers de code à partir de modèles de texte. Pour plus d’informations, consultez [génération du Code à l’aide de modèles de texte T4 au moment du Design](../modeling/design-time-code-generation-by-using-t4-text-templates.md) et [quelle est la meilleure façon de commencer à écrire un modèle ?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Générer des fichiers au moment de l’exécution, en passant des données dans le modèle
 Au moment de l’exécution, mon application génère des fichiers texte, tels que les rapports, qui contiennent un mélange de texte standard et les données. Je veux éviter d’écrire des centaines de `write` instructions.

-   Ajouter un modèle de texte runtime à votre projet. Ce modèle crée une classe dans votre code, vous pouvez instancier et utiliser pour générer du texte. Vous pouvez passer des données à celle-ci dans les paramètres du constructeur. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

-   Si vous souhaitez générer à partir de modèles qui sont uniquement disponibles au moment de l’exécution, vous pouvez utiliser des modèles de texte standard. Si vous écrivez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extension, vous pouvez appeler le service de création de modèles de texte. Pour plus d’informations, consultez [appeler la Transformation de texte dans une Extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). Dans d’autres contextes, vous pouvez utiliser le moteur de création de modèles de texte. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Utilisez le \<#@parameter#> directive pour passer des paramètres à ces modèles. Pour plus d’informations, consultez [Directive du paramètre T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Lire un autre fichier projet à partir d’un modèle
 Pour lire un fichier à partir de la même [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet comme modèle :

-   Insérez `hostSpecific="true"` dans la directive `<#@template#>`.

     Dans votre code, utilisez `this.Host.ResolvePath(filename)` pour obtenir le chemin d’accès complet du fichier.

### <a name="invoke-methods-from-a-template"></a>Appeler des méthodes à partir d’un modèle
 Si les méthodes existent déjà, par exemple, dans la norme [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] classes :

-   Utilisez le \<#@assembly#> la directive pour charger l’assembly et utiliser \<#@import#> pour définir le contexte de l’espace de noms. Pour plus d’informations, consultez [Directive d’importation T4](../modeling/t4-import-directive.md).

     Si vous fréquemment utilisez le même ensemble de l’assembly et directives d’importation, envisagez d’écrire un processeur de directive. Dans chaque modèle, vous pouvez appeler le processeur de directive, ce qui peut charger les assemblys et les fichiers de modèle et définir le contexte de l’espace de noms. Pour plus d’informations, consultez [création de processeurs de Directive de modèle personnalisé T4 texte](../modeling/creating-custom-t4-text-template-directive-processors.md).

 Si vous écrivez vous-même les méthodes :

-   Si vous écrivez un modèle de texte runtime, écrivez une définition de classe partielle qui porte le même nom que votre modèle de texte du runtime. Ajoutez les méthodes supplémentaires dans cette classe.

-   Écrire un bloc de contrôle de fonctionnalité de classe `<#+ ... #>` dans laquelle vous pouvez déclarer des méthodes, des propriétés et des classes privées. Lorsque le modèle de texte est compilé, il est transformé en une classe. Les blocs de contrôle standard `<#...#>` texte sont transformés en une seule méthode, et les blocs de fonctionnalité de classe sont insérés en tant que membres distincts. Pour plus d’informations, consultez [blocs de contrôle de modèle de texte](../modeling/text-template-control-blocks.md).

     Méthodes définies comme des fonctionnalités de la classe peuvent également inclure des blocs de texte incorporé.

     Envisagez de placer les fonctionnalités de la classe dans un fichier distinct que vous pouvez `<#@include#>` dans un ou plusieurs fichiers de modèle.

-   Les méthodes d’écriture dans un assembly séparé (bibliothèque de classes) et les appeler à partir de votre modèle. Utilisez le `<#@assembly#>` la directive pour charger l’assembly, et `<#@import#>` pour définir le contexte de l’espace de noms. Notez que pour régénérer l’assembly pendant que vous effectuez le débogage, vous devrez peut-être arrêter et redémarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [Directives de modèle de texte T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Générer de nombreux fichiers à partir d’un schéma de modèle
 Si vous générez souvent des fichiers à partir de modèles qui ont le même schéma XML ou de base de données :

-   Envisagez d’écrire un processeur de directive. Cela vous permet de remplacer plusieurs instructions assembly et l’importer dans chaque modèle avec une directive personnalisée unique. Le processeur de directive peut également charger et analyser le fichier de modèle. Pour plus d’informations, consultez [création de processeurs de Directive de modèle personnalisé T4 texte](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Générer des fichiers à partir d’un modèle complexe

-   Envisagez de créer un langage spécifique à un domaine (DSL) pour représenter le modèle. Cela rend beaucoup plus facile d’écrire les modèles, car vous utilisez des types et des propriétés qui reflètent les noms des éléments dans votre modèle. Vous n’avez pas à analyser le fichier ou de parcourir les nœuds XML. Par exemple :

     `foreach (Book book in this.Library) { ... }`

     Pour plus d’informations, consultez [prise en main de langages spécifiques à un domaine](../modeling/getting-started-with-domain-specific-languages.md) et [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Obtenez des données [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]
 Pour utiliser les services fournis dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par jeu le `hostSpecific` attribut et charge le `EnvDTE` assembly. Par exemple :

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

-   Pour plus d’informations, consultez [génération de Code dans un processus de génération](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Questions plus générales

###  <a name="starting"></a> Qu’est la meilleure façon de commencer à écrire un modèle de texte ?

1.  Écrivez un exemple spécifique du fichier généré.

2.  Transformer un modèle de texte en insérant la `<#@template #>` directive et les directives et code qui sont requises pour charger le fichier d’entrée ou le modèle.

3.  Remplacez progressivement des parties du fichier avec l’expression et les blocs de code.

### <a name="what-is-a-model"></a>Qu’est un « modèle » ?

-   L’entrée lue par votre modèle. Il peut être dans un fichier ou dans une base de données. Il peut être XML, ou un dessin Visio, ou un langage spécifique à un domaine (DSL) ou un modèle UML ou il peut s’agir de texte brut. Il peut être répartie sur plusieurs fichiers. En général, plusieurs modèles lit un modèle.

     La conséquence du « modèle » est qu’il représente un aspect de votre entreprise plus directement que le code de programme généré ou d’autres fichiers. Par exemple, il peut représenter le plan d’un réseau de communications vos logiciels générés seront supervise.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Quel est l’avantage d’utiliser des modèles de texte ?
 En règle générale, vous générez plusieurs code ou autres fichiers à partir d’un modèle. Le modèle représente les spécifications plus directement que le code généré. Elle omet le détail d’implémentation et est écrit en termes de la configuration requise, plutôt que le code. Lorsque les besoins changent - comme ils le font généralement - vous pouvez mettre à jour le modèle plus facilement et plus fiable que les différentes parties du code du programme.

 Génération de code est donc un outil précieux du point de vue des méthodes de développement agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Les « meilleures pratiques » sont de modèles de texte ?

-   Pour plus d’informations, consultez [des recommandations pour les modèles de texte T4 écrit](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Qu’est « T4 » ?

-   Un autre nom pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fonctionnalités de modèle de texte décrites ici. La version précédente, ce qui n’était pas publiée, est l’abréviation de « Transformation du modèle de texte ».
