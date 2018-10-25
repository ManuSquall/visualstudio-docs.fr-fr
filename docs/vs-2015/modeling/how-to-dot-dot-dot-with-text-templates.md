---
title: Comment... avec des modèles de texte | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8e6a580a906ea228f04f8ec81b15eee6c143c6a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903814"
---
# <a name="how-to--with-text-templates"></a>Comment : écrire avec des modèles de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modèles de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offrent un moyen utile de générer du texte de n’importe quel type. Vous pouvez utiliser des modèles de texte pour générer du texte en cours d’exécution dans le cadre de votre application et au moment du design pour générer une partie de votre code de projet. Cette rubrique récapitule les plus fréquemment posées « Comment faire... ? » questions.  
  
 Dans cette rubrique, les réponses multiples qui sont précédés de puces sont des suggestions alternatives.  
  
 Pour une introduction générale aux modèles de texte, consultez [génération de Code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Comment...  
  
### <a name="generate-part-of-my-application-code"></a>Générer une partie de mon code d’application  
 J’ai une configuration ou *modèle* dans un fichier ou une base de données. Une ou plusieurs parties de mon code dépendent de ce modèle.  
  
-   Générer certaines de vos fichiers de code à partir de modèles de texte. Pour plus d’informations, consultez [génération de Code au moment du Design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) et [quelle est la meilleure façon de commencer à écrire un modèle ?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Générer des fichiers en cours d’exécution, en passant des données dans le modèle  
 Au moment de l’exécution, mon application génère des fichiers texte, tels que des rapports, qui contiennent un mélange de texte standard et les données. Je souhaite éviter d’écrire des centaines de `write` instructions.  
  
-   Ajouter un modèle de texte du runtime à votre projet. Ce modèle crée une classe dans votre code, que vous pouvez instancier et utiliser pour générer du texte. Vous pouvez passer des données à ce dernier dans les paramètres du constructeur. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Si vous souhaitez générer à partir de modèles qui sont uniquement disponibles au moment de l’exécution, vous pouvez utiliser des modèles de texte standard. Si vous écrivez un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension, vous pouvez appeler le service de création de modèles de texte. Pour plus d’informations, consultez [appel d’une Transformation de texte dans une Extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). Dans d’autres contextes, vous pouvez utiliser le moteur de création de modèles de texte. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.  
  
     Utilisez le \<#@parameter#> directive pour transmettre des paramètres à ces modèles. Pour plus d’informations, consultez [Directive du paramètre T4](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Lire un autre fichier projet à partir d’un modèle  
 Pour lire un fichier à partir de la même [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet comme modèle :  
  
-   Insérez `hostSpecific="true"` dans la directive `<#@template#>`.  
  
     Dans votre code, utilisez `this.Host.ResolvePath(filename)` pour obtenir le chemin d’accès complet du fichier.  
  
### <a name="invoke-methods-from-a-template"></a>Appeler des méthodes à partir d’un modèle  
 Si les méthodes existent déjà, par exemple, dans la norme [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] classes :  
  
- Utiliser le \<#@assembly#> la directive pour charger l’assembly, utilisez \<#@import#> pour définir le contexte de l’espace de noms. Pour plus d’informations, consultez [Directive d’importation T4](../modeling/t4-import-directive.md).  
  
   Si fréquemment, vous utilisez le même ensemble de l’assembly et importez des directives, envisagez d’écrire un processeur de directive. Dans chaque modèle, vous pouvez appeler le processeur de directive, ce qui peut charger les assemblys et les fichiers de modèle et définir le contexte de l’espace de noms. Pour plus d’informations, consultez [processeurs de Directive modèles de création personnalisé T4 texte](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
  Si vous écrivez vous-même les méthodes :  
  
- Si vous écrivez un modèle de texte de runtime, écrivez une définition de classe partielle qui a le même nom que votre modèle de texte de runtime. Ajoutez les méthodes supplémentaires dans cette classe.  
  
- Écrire un bloc de contrôle de fonctionnalité de classe `<#+ ... #>` dans lequel vous pouvez déclarer méthodes, propriétés et classes privées. Lorsque le modèle de texte est compilé, il est transformé en une classe. Les blocs de contrôle standard `<#...#>` texte sont transformées en une seule méthode, et les blocs de fonctionnalité de classe sont insérés en tant que membres distincts. Pour plus d’informations, consultez [blocs de contrôle de modèles de texte](../modeling/text-template-control-blocks.md).  
  
   Méthodes définies comme des fonctionnalités de la classe peuvent également inclure des blocs de texte incorporé.  
  
   Envisagez de placer les fonctionnalités de la classe dans un fichier distinct que vous pouvez `<#@include#>` dans un ou plusieurs fichiers de modèle.  
  
- Écrire les méthodes dans un assembly séparé (bibliothèque de classes) et les appeler à partir de votre modèle. Utilisez le `<#@assembly#>` directive pour charger l’assembly, et `<#@import#>` pour définir le contexte de l’espace de noms. Notez que pour régénérer l’assembly pendant que vous le déboguez, vous devrez peut-être arrêter et redémarrer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Directives de modèles de texte T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Générer de nombreux fichiers à partir d’un schéma de modèle  
 Si vous générez souvent des fichiers à partir de modèles qui ont le même schéma XML ou de base de données :  
  
-   Envisager d’écrire un processeur de directive. Cela vous permet de remplacer plusieurs instructions assembly et import dans chaque modèle avec une directive personnalisée unique. Le processeur de directive peut également charger et analyser le fichier de modèle. Pour plus d’informations, consultez [processeurs de Directive modèles de création personnalisé T4 texte](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Générer des fichiers à partir d’un modèle complexe  
  
-   Envisagez de créer un langage spécifique à un domaine (DSL) pour représenter le modèle. Cela rend beaucoup plus facile d’écrire les modèles, car vous utilisez des types et des propriétés qui reflètent les noms des éléments dans votre modèle. Vous n’avez pas à analyser le fichier ou de parcourir les nœuds XML. Exemple :  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Pour plus d’informations, consultez [mise en route avec les langages spécifiques à un domaine](../modeling/getting-started-with-domain-specific-languages.md) et [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   Envisagez de générer du code à partir d’un modèle UML. Le code n’a pas refléter l’UML directement. Par exemple, vous n’êtes pas obligé de générer une classe pour chaque classe dans le modèle UML. Au lieu de cela, vous pouvez utiliser le diagramme de classes UML pour représenter un site web et générer une page web à partir de chaque classe UML. Choisissez le type de diagramme le plus proche de vos besoins. Par exemple, choisir les diagrammes d’activités pour représenter n’importe quel type de flux de travail. Vous pouvez définir des stéréotypes pour ajouter les informations appropriées à votre application pour chaque type d’élément.  
  
     Génération à partir d’un modèle UML vous permet de dessiner et de modifier le modèle schématique, mais sans avoir à concevoir votre propre type de diagramme, comme vous le feriez avec une solution DSL.  
  
     Pour plus d’informations, consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md) et [générer des fichiers à partir d’un modèle UML](../modeling/generate-files-from-a-uml-model.md).  
  
### <a name="get-data-from-includevsprvsincludesvsprvs-mdmd"></a>Obtenir des données à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
 Pour utiliser les services fournis dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], par jeu la `hostSpecific` attribut et charge le `EnvDTE` assembly. Exemple :  
  
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
  
###  <a name="starting"></a> Quel est le meilleur moyen pour commencer à écrire un modèle de texte ?  
  
1.  Écrire un exemple spécifique du fichier généré.  
  
2.  Transformer en un modèle de texte en insérant la `<#@template #>` directive et les directives et code qui sont requis pour charger le fichier d’entrée ou le modèle.  
  
3.  Remplacez progressivement des parties du fichier avec expression et les blocs de code.  
  
### <a name="what-is-a-model"></a>Qu’est un « modèle » ?  
  
-   L’entrée lue par votre modèle. Il peut être dans un fichier ou dans une base de données. Il peut être XML, ou un dessin Visio, ou un langage spécifique à un domaine (DSL) ou un modèle UML, ou il peut s’agir de texte brut. Il pourrait être répartie sur plusieurs fichiers. En général, plusieurs modèles lit un seul modèle.  
  
     La conséquence de « modèle » est qu’elle représente un aspect de votre entreprise plus directement que le code du programme généré ou d’autres fichiers. Par exemple, il peut représenter le plan d’un réseau de communications, chargés de superviser sera votre logiciel généré.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Quel est l’avantage de l’utilisation de modèles de texte ?  
 En règle générale, vous générez plusieurs code ou autres fichiers à partir d’un modèle. Le modèle représente les spécifications plus directement que le code généré. Il omet le détail d’implémentation et est écrit en termes de la configuration requise, plutôt que le code. Lorsque les spécifications changent, comme ils le font généralement – vous pouvez mettre à jour le modèle plus facilement et plus fiable que les différentes parties du code du programme.  
  
 Génération de code est donc un outil précieux du point de vue des méthodes de développement agile.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Les « meilleures pratiques » existe-t-il pour les modèles de texte ?  
  
-   Pour plus d’informations, consultez [instructions pour l’écriture de modèles de texte T4](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Qu’est « T4 » ?  
  
-   Un autre nom pour le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les fonctionnalités de modèle de texte décrites ici. La version précédente, ce qui n’était pas publiée, a été une abréviation de « Transformation de modèle de texte ».



