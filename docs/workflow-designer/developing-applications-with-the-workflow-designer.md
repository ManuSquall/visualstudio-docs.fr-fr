---
title: "D&#233;veloppement d&#39;applications avec Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Visual Studio 2010 Workflow Designer [WFD]"
  - "Visual Studio 2010 Workflow Designer [WFD], vue d'ensemble"
  - "Workflow Designer [WFD]"
  - "Workflow Designer [WFD], vue d'ensemble"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# D&#233;veloppement d&#39;applications avec Workflow Designer
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] est un concepteur visuel et un débogueur pour la construction graphique et le débogage d'applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] hébergé dans l'environnement de développement [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Il vous permet de composer une application de workflow composite, une bibliothèque d'activités ou un service [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] via l'utilisation de modèles et de concepteurs d'activités.[!INCLUDE[crabout](../test/includes/crabout_md.md)] les workflows, consultez [Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md).  
  
 Voici plusieurs nouvelles fonctionnalités de conception qui distinguent cette nouvelle version de[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] des versions antérieures de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] :  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] est construit à l'aide de [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)].Cela améliore l'expérience des concepteurs d'activités et les performances des workflows grands et complexes.  
  
-   Les activités personnalisées sont maintenant conçues avec [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], à l'aide de XAML, et le modèle de programmation pour la création de concepteurs d'activités a été simplifié.  
  
-   Une activité d'organigramme a été implémentée, afin de vous permettre de visualiser le flux du programme à l'aide du style de modélisation d'organigramme habituel.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dispose d'un nouveau concepteur de variables qui vous permet de déclarer et de limiter des variables dans vos workflows, en les liant à des activités.  
  
-   Dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fournit des fonctionnalités IntelliSense complètes lors de la création d'expressions Visual Basic dans vos workflows [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   L'expérience de débogage s'étend maintenant en XAML, ce qui vous permet de définir des points d'arrêt dans votre définition de workflow XAML et d'effectuer un pas à pas détaillé dans votre code XAML au moment de l'exécution, ce qui fournit une expérience comparable à celle que procure le code managé.  
  
-   Le réhébergement de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hors de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est considérablement simplifié par rapport aux versions précédentes, ne nécessitant maintenant que quelques lignes de code.  
  
-   La nouvelle activité <xref:System.Activities.Statements.Flowchart> et son [Organigramme](../workflow-designer/flowchart-activity-designer.md) vous permettent de visualiser votre flux de programme à l'aide du style de modélisation d'organigramme habituel.  
  
-   Les activités de messagerie ont été améliorées, vous permettant d'écrire des services [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] entièrement déclaratifs \(sans code\).  
  
-   La fonctionnalité **Ajouter une référence de service** vous permet de générer automatiquement des activités qui accèdent aux services Web.  
  
## Dans cette section  
 [Utilisation de Workflow Designer](../workflow-designer/using-the-workflow-designer.md)  
 Indique comment créer de nouvelles activités et des projets de workflow à l'aide des concepteurs intégrés et comment utiliser les autres outils fournis par le concepteur pour gérer les arguments, les variables, les expressions, les importations et l'exploration à l'aide de la barre de navigation.  
  
 [Utilisation des concepteurs d'activités](../workflow-designer/using-the-activity-designers.md)  
 Décrit les catégories d'activités et de modèles et leurs concepteurs, fournis par le système.  
  
 [Débogage de workflows avec Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Explique comment exécuter des procédures de débogage traditionnelles, ainsi que le débogage de code XAML et d'expressions.  
  
 [Aide sur l'interface utilisateur de Workflow Designer](../workflow-designer/workflow-designer-ui-help.md)  
 Contient des rubriques d'aide contextuelle relatives aux boîtes de dialogue fournies par [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], ainsi qu'une aide sur les fonctionnalités du shell du concepteur, les raccourcis clavier et les messages d'erreur.  
  
 [Développement d'applications de workflow qui ciblent le .NET 3.0 ou .NET 3.5 Framework](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contient de l'aide sur l'utilisation du concepteur hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Réhébergement du concepteur &#91;exemples WF&#93;](../Topic/Designer%20ReHosting.md)  
 Cet exemple indique comment créer la disposition WPF pour contenir le concepteur.  
  
 [Concepteurs d'activités personnalisées](../Topic/Custom%20Activity%20Designers.md)  
 Cette section contient des exemples d'activités qui utilisent des concepteurs personnalisés pour l'affichage dans le concepteur de workflow.