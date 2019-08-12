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
ms.openlocfilehash: 1c8f306315ad236843b6fcd5551d9aed13c26a92
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871786"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Traitement des modèles de texte à l'aide d'un hôte personnalisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le processus de *transformation de modèle de texte* utilise un fichier de modèle de *texte* comme entrée et produit un fichier texte comme sortie. Vous pouvez appeler le moteur de transformation de texte à partir d'une extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou d'une application autonome s'exécutant sur un ordinateur où [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est installé. Toutefois, vous devez fournir un *hôte de création de modèles de texte*. Cette classe connecte le modèle à l'environnement, recherchant des ressources telles que les assemblys et les fichiers Include, et traitant les messages d'erreur et de sortie.

> [!TIP]
> Si vous écrivez un package ou une extension qui s’exécutera dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], envisagez d’utiliser le service de création de modèles de texte, plutôt que d’écrire dans votre propre hôte. Pour plus d’informations, consultez [appel de la transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Il est préférable de ne pas utiliser les transformations de modèle de texte dans les applications serveur. Il est déconseillé de les employer, sauf dans un thread unique. En effet, le moteur de création de modèles de texte réutilise un AppDomain unique pour traduire, compiler et exécuter des modèles. Le code traduit n'a pas été conçu pour être thread-safe. Le moteur a été conçu pour traiter des fichiers de façon séquentielle, lorsqu'ils sont dans un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] au moment du design.
>
> Pour les applications au moment de l’exécution, envisagez d’utiliser des modèles de texte prétraités: consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Si votre application utilise un ensemble de modèles fixés au moment de la compilation, il est plus facile d'employer des modèles de texte prétraités. Vous pouvez également utiliser cette approche si votre application doit s'exécuter sur un ordinateur où [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] n'est pas installé. Pour plus d’informations, consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="executing-a-text-template-in-your-application"></a>Exécution d'un modèle de texte dans votre application
 Pour exécuter un modèle de texte, vous pouvez appeler la méthode ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Votre application doit rechercher et fournir le modèle, de même que traiter la sortie.

 Dans le `host` paramètre, vous devez fournir une classe qui implémente [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Celle-ci est rappelée par le moteur.

 L'hôte doit être en mesure de consigner les erreurs, de résoudre les références à l'assembly et aux fichiers Include, de fournir un domaine d'application dans lequel le modèle peut s'exécuter et d'appeler le processeur approprié pour chaque directive.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>est défini dans **Microsoft. VisualStudio. TextTemplating.\*. 0. dll**et [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) sont définis dans **Microsoft. VisualStudio. TextTemplating. interfaces.\* 0. dll**.

## <a name="in-this-section"></a>Dans cette section
 [Procédure pas à pas : La création d’un hôte](../modeling/walkthrough-creating-a-custom-text-template-host.md) de modèle de texte personnalisé vous montre comment créer un hôte de modèle de texte personnalisé qui rend la fonctionnalité de modèle de texte disponible en dehors [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]de.

## <a name="reference"></a>Référence
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Rubriques connexes
 [Processus de transformation du modèle de texte](../modeling/the-text-template-transformation-process.md) Décrit le fonctionnement de la transformation de texte et les parties que vous pouvez personnaliser.

 [Création de processeurs de directive de modèle de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md) Fournit une vue d’ensemble des processeurs de directive de modèle de texte.
