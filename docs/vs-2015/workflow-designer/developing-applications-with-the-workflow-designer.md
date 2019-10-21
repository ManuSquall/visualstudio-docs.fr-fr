---
title: Développement d’applications avec le Concepteur de flux de travail | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656826"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Développement d'applications avec Workflow Designer
[!INCLUDE[wfd1](../includes/wfd1-md.md)] est un concepteur visuel et un débogueur pour la construction graphique et le débogage d'applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] hébergé dans l'environnement de développement [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Il vous permet de composer une application de workflow composite, une bibliothèque d'activités ou un service [!INCLUDE[indigo1](../includes/indigo1-md.md)] via l'utilisation de modèles et de concepteurs d'activités. [!INCLUDE[crabout](../includes/crabout-md.md)] des flux de travail, consultez les [ &#91;Windows Workflow Foundation&#93;.NET Framework 4](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Voici plusieurs nouvelles fonctionnalités de conception qui distinguent cette nouvelle version de[!INCLUDE[wfd2](../includes/wfd2-md.md)] des versions antérieures de [!INCLUDE[wfd2](../includes/wfd2-md.md)] :

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] est construit à l'aide de [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Cela améliore l'expérience des concepteurs d'activités et les performances des workflows grands et complexes.

- Les activités personnalisées sont maintenant conçues avec [!INCLUDE[avalon2](../includes/avalon2-md.md)], à l'aide de XAML, et le modèle de programmation pour la création de concepteurs d'activités a été simplifié.

- Une activité d'organigramme a été implémentée, afin de vous permettre de visualiser le flux du programme à l'aide du style de modélisation d'organigramme habituel.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] dispose d'un nouveau concepteur de variables qui vous permet de déclarer et de limiter des variables dans vos workflows, en les liant à des activités.

- Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] fournit des fonctionnalités IntelliSense complètes lors de la création d'expressions Visual Basic dans vos workflows [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

- L'expérience de débogage s'étend maintenant en XAML, ce qui vous permet de définir des points d'arrêt dans votre définition de workflow XAML et d'effectuer un pas à pas détaillé dans votre code XAML au moment de l'exécution, ce qui fournit une expérience comparable à celle que procure le code managé.

- Le réhébergement de [!INCLUDE[wfd2](../includes/wfd2-md.md)] hors de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est considérablement simplifié par rapport aux versions précédentes, ne nécessitant maintenant que quelques lignes de code.

- La nouvelle activité <xref:System.Activities.Statements.Flowchart> et son [organigramme](../workflow-designer/flowchart-activity-designer.md) vous permettent de visualiser le flux de votre programme à l’aide du style de modélisation organigramme familier.

- Les activités de messagerie ont été améliorées, vous permettant d'écrire des services [!INCLUDE[indigo1](../includes/indigo1-md.md)] entièrement déclaratifs (sans code).

- La **Ajouter une référence de service...** la fonctionnalité vous permet de générer automatiquement des activités qui accèdent aux services Web.

## <a name="in-this-section"></a>Dans cette section
 [Utilisation de l’Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md) Montre comment créer des activités et des projets de workflow à l’aide des concepteurs intégrés et comment utiliser d’autres outils fournis par le concepteur pour gérer les arguments, les variables, les expressions, les importations et la navigation dans le fil.

 [Utilisation des concepteurs d’activités](../workflow-designer/using-the-activity-designers.md) Décrit les catégories d’activités et de modèles et leurs concepteurs fournis par le système.

 [Débogage de flux de travail avec le concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Explique comment effectuer des procédures de débogage traditionnelles et déboguer du code XAML et des expressions.

 [Aide sur l’interface utilisateur concepteur de flux de travail](../workflow-designer/workflow-designer-ui-help.md) Contient des rubriques d’aide contextuelle pour les boîtes de dialogue fournies par [!INCLUDE[wfd1](../includes/wfd1-md.md)], ainsi que des conseils sur les fonctionnalités du shell du concepteur, les raccourcis clavier et les messages d’erreur.

 [Développement d’applications de workflow ciblant l’infrastructure .net 3,0 ou .net 3,5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Contient des conseils sur l’utilisation du concepteur hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [Réhébergement par le &#91;concepteur d'&#93; exemples WF](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) Cet exemple montre comment créer la disposition WPF pour contenir le concepteur.

 [Concepteurs d’activités personnalisées](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Cette section contient des exemples d’activités qui utilisent des concepteurs personnalisés pour l’affichage dans le concepteur de Workflow.