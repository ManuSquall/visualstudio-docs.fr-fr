---
title: "Développement d’Applications avec le Concepteur de flux de travail | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: cbb7b09e5c36980ceeedd99f69241996bd25bfa3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>Développement d'applications avec Workflow Designer
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] est un concepteur visuel et un débogueur pour la construction graphique et le débogage d'applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] hébergé dans l'environnement de développement [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Il vous permet de composer une application de workflow composite, une bibliothèque d'activités ou un service [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] via l'utilisation de modèles et de concepteurs d'activités. [!INCLUDE[crabout](../test/includes/crabout_md.md)]flux de travail, consultez le [Windows Workflow Foundation &#91;. .NET Framework 4 &#93; ](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
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
  
## <a name="in-this-section"></a>Dans cette section  
 [Utilisation du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)  
 Indique comment créer de nouvelles activités et des projets de workflow à l'aide des concepteurs intégrés et comment utiliser les autres outils fournis par le concepteur pour gérer les arguments, les variables, les expressions, les importations et l'exploration à l'aide de la barre de navigation.  
  
 [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md)  
 Décrit les catégories d'activités et de modèles et leurs concepteurs, fournis par le système.  
  
 [Débogage de flux de travail à l’aide du Concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Explique comment exécuter des procédures de débogage traditionnelles, ainsi que le débogage de code XAML et d'expressions.  
  
 [Aide sur l’interface utilisateur du Concepteur de flux de travail](../workflow-designer/workflow-designer-ui-help.md)  
 Contient des rubriques d'aide contextuelle relatives aux boîtes de dialogue fournies par [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], ainsi qu'une aide sur les fonctionnalités du shell du concepteur, les raccourcis clavier et les messages d'erreur.  
  
 [Développement d’applications de flux de travail qui ciblent le .NET Framework 3.0 ou 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contient de l'aide sur l'utilisation du concepteur hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Réhébergement du Concepteur &#91; Exemples WF &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 Cet exemple indique comment créer la disposition WPF pour contenir le concepteur.  
  
 [Concepteurs d’activités personnalisées](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 Cette section contient des exemples d'activités qui utilisent des concepteurs personnalisés pour l'affichage dans le concepteur de workflow.