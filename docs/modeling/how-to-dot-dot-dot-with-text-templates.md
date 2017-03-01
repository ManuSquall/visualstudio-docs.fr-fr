---
title: "Comment : écrire avec des modèles de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>Comment : écrire avec des modèles de texte
Modèles de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournissent un moyen utile de générer du texte de n’importe quel type. Vous pouvez utiliser des modèles de texte pour générer du texte au moment de l’exécution dans le cadre de votre application et au moment du design pour générer du code de votre projet. Cette rubrique résume les plus fréquemment posées « Comment... ? » questions.  
  
 Dans cette rubrique, les réponses multiples précédées par des puces sont des suggestions alternatives.  
  
 Pour une introduction générale aux modèles de texte, consultez [génération de Code et de modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Comment...  
  
### <a name="generate-part-of-my-application-code"></a>Générer une partie de mon code d’application  
 Disposez d’une configuration ou *modèle* dans un fichier ou une base de données. Une ou plusieurs parties de mon code dépendent de ce modèle.  
  
-   Générez certains de vos fichiers de code à partir de modèles de texte. Pour plus d’informations, consultez [génération du Code à l’aide de modèles de texte T4 au moment du Design](../modeling/design-time-code-generation-by-using-t4-text-templates.md) et [quelle est la meilleure façon de commencer à écrire un modèle ?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Générer des fichiers au moment de l’exécution, en passant des données dans le modèle  
 Au moment de l’exécution, mon application génère des fichiers texte, tels que des rapports, qui contiennent un mélange de texte standard et des données. Je souhaite éviter d’écrire des centaines de `write` instructions.  
  
-   Ajouter un modèle de texte runtime à votre projet. Ce modèle crée une classe dans votre code, vous pouvez instancier et utiliser pour générer du texte. Vous pouvez passer des données à celle-ci dans les paramètres du constructeur. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Si vous souhaitez générer à partir de modèles qui sont uniquement disponibles au moment de l’exécution, vous pouvez utiliser des modèles de texte standard. Si vous écrivez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extension, vous pouvez appeler le service de création de modèles de texte. Pour plus d’informations, consultez [appeler la Transformation de texte dans une Extension Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md). Dans d’autres contextes, vous pouvez utiliser le moteur de création de modèles de texte. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     Utilisez le \<#@parameter#> directive pour passer des paramètres à ces modèles. Pour plus d’informations, consultez [Directive du paramètre T4](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Lire un autre fichier de projet à partir d’un modèle  
 Pour lire un fichier à partir de la même [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet comme modèle :  
  
-   Insérez `hostSpecific="true"` dans la directive `<#@template#>`.  
  
     Dans votre code, utilisez `this.Host.ResolvePath(filename)` pour obtenir le chemin d’accès complet du fichier.  
  
### <a name="invoke-methods-from-a-template"></a>Appeler des méthodes à partir d’un modèle  
 Si les méthodes existent déjà, par exemple, dans la norme [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] classes :  
  
-   Utilisez le \<#@assembly#> directive pour charger l’assembly, utilisez \<#@import#> pour définir le contexte de l’espace de noms. Pour plus d’informations, consultez [Directive d’importation T4](../modeling/t4-import-directive.md).  
  
     Si vous fréquemment utilisez le même ensemble de l’assembly et directives d’importation, envisagez d’écrire un processeur de directive. Dans chaque modèle, vous pouvez appeler le processeur de directive peut charger les assemblys et les fichiers de modèle et définir le contexte de l’espace de noms. Pour plus d’informations, consultez [créer les processeurs de Directive personnalisés T4 texte modèle](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Si vous écrivez vous-même les méthodes :  
  
-   Si vous écrivez un modèle de texte runtime, écrivez une définition de classe partielle qui porte le même nom que votre modèle de texte runtime. Ajoutez les méthodes supplémentaires à cette classe.  
  
-   Écrire un bloc de contrôle de fonctionnalité de classe `<#+ ... #>` dans lequel vous pouvez déclarer des méthodes, propriétés et des classes privées. Lorsque le modèle de texte est compilé, il est transformé en classe. Les blocs de contrôle standard `<#...#>` et texte sont transformées en une seule méthode, et les blocs de fonctionnalité de classe sont insérés en tant que membres distincts. Pour plus d’informations, consultez [blocs de contrôle de modèle de texte](../modeling/text-template-control-blocks.md).  
  
     Méthodes définies comme des fonctionnalités de la classe peuvent également inclure des blocs de texte incorporés.  
  
     Envisagez de placer les fonctionnalités de la classe dans un fichier distinct qui peut être `<#@include#>` dans un ou plusieurs fichiers de modèle.  
  
-   Les méthodes d’écriture dans un assembly séparé (bibliothèque de classes) et les appeler à partir de votre modèle. Utilisez le `<#@assembly#>` directive pour charger l’assembly, et `<#@import#>` pour définir le contexte de l’espace de noms. Notez que pour régénérer l’assembly pendant que vous le déboguez, vous devrez peut-être arrêter et redémarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [Directives de modèles de texte T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Générer de nombreux fichiers à partir d’un schéma de modèle  
 Si vous générez souvent des fichiers à partir de modèles qui ont le même schéma XML ou de base de données :  
  
-   Envisagez d’écrire un processeur de directive. Cela vous permet de remplacer plusieurs instructions assembly et import dans chaque modèle avec une directive personnalisée unique. Le processeur de directive peut également charger et analyser le fichier de modèle. Pour plus d’informations, consultez [créer les processeurs de Directive personnalisés T4 texte modèle](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Générer des fichiers à partir d’un modèle complexe  
  
-   Envisagez de créer un langage spécifique à un domaine (DSL) pour représenter le modèle. Cela rend beaucoup plus facile d’écrire les modèles, car vous utilisez des types et des propriétés qui reflètent les noms des éléments dans votre modèle. Vous n’avez pas à analyser le fichier ou de parcourir les nœuds XML. Exemple :  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Pour plus d’informations, consultez [mise en route avec les langages spécifiques au domaine](../modeling/getting-started-with-domain-specific-languages.md) et [génération du Code à partir d’un langage spécifique au domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Obtenir des données à partir de[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Pour utiliser les services fournis dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par ensemble le `hostSpecific` attribut et charge le `EnvDTE` assembly. Exemple :  
  
```c#  
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
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>Quelle est la meilleure façon pour commencer à écrire un modèle de texte ?  
  
1.  Écrivez un exemple spécifique du fichier généré.  
  
2.  Transformer en un modèle de texte en insérant la `<#@template #>` directive et les directives et code qui sont requis pour charger le fichier d’entrée ou le modèle.  
  
3.  Remplacez progressivement des parties du fichier avec expression et les blocs de code.  
  
### <a name="what-is-a-model"></a>Qu’est un « modèle » ?  
  
-   L’entrée lue par votre modèle. Il peut être dans un fichier ou dans une base de données. Il peut être XML, ou un dessin Visio, ou un langage spécifique à un domaine (DSL) ou un modèle UML ou il peut s’agir de texte brut. Il pourrait être répartie sur plusieurs fichiers. Plusieurs modèles lit généralement un modèle.  
  
     La conséquence de « modèle » est qu’il représente un aspect de votre entreprise plus directement que le code généré du programme ou d’autres fichiers. Par exemple, il peut représenter le plan d’un réseau de communications que vos logiciels générés surveilleront.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Quel est l’avantage de l’utilisation de modèles de texte ?  
 En général, vous générez plusieurs code ou autres fichiers à partir d’un modèle. Le modèle représente les spécifications plus directement que le code généré. Il omet le détail d’implémentation et est écrit en termes d’exigences, plutôt que dans le code. Lorsque les spécifications changent, comme ils le font généralement – vous pouvez mettre à jour le modèle plus facilement et plus fiable que les différentes parties du code du programme.  
  
 Génération de code est par conséquent un outil précieux du point de vue des méthodes de développement agiles.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Les « meilleures pratiques » sont de modèles de texte ?  
  
-   Pour plus d’informations, consultez [les instructions pour les modèles de texte T4 écrit](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Quel est le « T4 » ?  
  
-   Un autre nom pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fonctionnalités de modèle de texte décrites ici. La version précédente, ce qui n’était pas publiée, a été une abréviation de « Transformation du modèle de texte ».

