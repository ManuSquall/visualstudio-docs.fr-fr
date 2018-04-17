---
title: Développement d’Applications avec le Concepteur de flux de travail | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c48e7b43b23e7bfe8887f437cc17e6db077c0e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Développement d'applications avec Workflow Designer

Le Concepteur de flux de travail de Windows est un concepteur visuel et le débogueur pour la construction graphique et le débogage de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] applications dans le [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] qui est hébergé dans le [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] environnement de développement. Il vous permet de composer une application de workflow composite, une bibliothèque d'activités ou un service [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] via l'utilisation de modèles et de concepteurs d'activités. Pour plus d’informations sur les workflows, consultez le [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Voici plusieurs nouvelles fonctionnalités de conception qui distinguent cette nouvelle version de[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] des versions antérieures de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] :

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] est construit à l'aide de [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Cela améliore l'expérience des concepteurs d'activités et les performances des workflows grands et complexes.

-   Les activités personnalisées sont maintenant conçues avec [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], à l'aide de XAML, et le modèle de programmation pour la création de concepteurs d'activités a été simplifié.

-   Une activité d'organigramme a été implémentée, afin de vous permettre de visualiser le flux du programme à l'aide du style de modélisation d'organigramme habituel.

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dispose d'un nouveau concepteur de variables qui vous permet de déclarer et de limiter des variables dans vos workflows, en les liant à des activités.

-   Dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fournit des fonctionnalités IntelliSense complètes lors de la création d'expressions Visual Basic dans vos workflows [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].

-   L'expérience de débogage s'étend maintenant en XAML, ce qui vous permet de définir des points d'arrêt dans votre définition de workflow XAML et d'effectuer un pas à pas détaillé dans votre code XAML au moment de l'exécution, ce qui fournit une expérience comparable à celle que procure le code managé.

-   Le réhébergement de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est considérablement simplifié par rapport aux versions précédentes, ne nécessitant maintenant que quelques lignes de code.

-   La nouvelle <xref:System.Activities.Statements.Flowchart> activité et ses [organigramme](../workflow-designer/flowchart-activity-designer.md) vous permettent de visualiser votre flux de programme à l’aide de l’organigramme style de modélisation.

-   Les activités de messagerie ont été améliorées, vous permettant d'écrire des services [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] entièrement déclaratifs (sans code).

-   Le **ajouter une référence de Service...**  fonctionnalité vous permet de générer automatiquement des activités qui accèdent aux services Web.