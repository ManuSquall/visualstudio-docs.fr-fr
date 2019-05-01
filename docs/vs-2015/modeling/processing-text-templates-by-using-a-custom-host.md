---
title: Traitement des modèles de texte à l’aide d’un hôte personnalisé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e9f27d203f317a63049015dbeba073d8ee075e61
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428073"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Traitement des modèles de texte à l'aide d'un hôte personnalisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le *transformation du modèle de texte* traiter prend un *modèle de texte* fichier comme entrée et produit un fichier texte comme sortie. Vous pouvez appeler le moteur de transformation de texte à partir d'une extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou d'une application autonome s'exécutant sur un ordinateur où [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est installé. Toutefois, vous devez fournir un *hôte de modèles de texte*. Cette classe connecte le modèle à l'environnement, recherchant des ressources telles que les assemblys et les fichiers Include, et traitant les messages d'erreur et de sortie.  
  
> [!TIP]
> Si vous écrivez un package ou une extension qui s’exécutera dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], envisagez d’utiliser le service de création de modèles de texte, plutôt que d’écrire dans votre propre hôte. Pour plus d’informations, consultez [appel d’une Transformation de texte dans une Extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
> Il est préférable de ne pas utiliser les transformations de modèle de texte dans les applications serveur. Il est déconseillé de les employer, sauf dans un thread unique. En effet, le moteur de création de modèles de texte réutilise un AppDomain unique pour traduire, compiler et exécuter des modèles. Le code traduit n'a pas été conçu pour être thread-safe. Le moteur a été conçu pour traiter des fichiers de façon séquentielle, lorsqu'ils sont dans un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] au moment du design.  
>   
> Pour les applications de l’exécution, envisagez d’utiliser des modèles de texte prétraités : consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Si votre application utilise un ensemble de modèles fixés au moment de la compilation, il est plus facile d'employer des modèles de texte prétraités. Vous pouvez également utiliser cette approche si votre application doit s'exécuter sur un ordinateur où [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] n'est pas installé. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="executing-a-text-template-in-your-application"></a>Exécution d'un modèle de texte dans votre application  
 Pour exécuter un modèle de texte, vous pouvez appeler la méthode ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 Votre application doit rechercher et fournir le modèle, de même que traiter la sortie.  
  
 Dans le paramètre `host`, vous devez fournir une classe qui implémente l'interface <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Celle-ci est rappelée par le moteur.  
  
 L'hôte doit être en mesure de consigner les erreurs, de résoudre les références à l'assembly et aux fichiers Include, de fournir un domaine d'application dans lequel le modèle peut s'exécuter et d'appeler le processeur approprié pour chaque directive.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> est défini dans **Microsoft.VisualStudio.TextTemplating.\*. 0.log dll de**, et <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> est défini dans **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0.log dll de**.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure pas à pas : Créer un hôte de modèle de texte personnalisé](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Indique comment créer un hôte de modèle de texte personnalisé qui rend la fonctionnalité de modèle de texte disponible en dehors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Processus de transformation du modèle de texte](../modeling/the-text-template-transformation-process.md)  
 Décrit le fonctionnement de la transformation de texte et indique les parties que vous pouvez personnaliser.  
  
 [Création de processeurs de directives de modèles de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Fournit une vue d'ensemble des processeurs de directive de modèle de texte.
