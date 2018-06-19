---
title: Développement d'applications avec Workflow Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970123"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Développement d'applications avec Workflow Designer

Le Concepteur de flux de travail de Windows est un concepteur visuel et le débogueur pour la construction graphique et le débogage des applications Windows Workflow Foundation (WF) dans le .NET Framework 4 qui est hébergé dans l’environnement de développement Visual Studio 2010. Il vous permet de composer une application de workflow composite, une bibliothèque d’activités ou un service Windows Communication Foundation (WCF) via l’utilisation de modèles et les concepteurs d’activités. Pour plus d’informations sur les workflows, consultez le [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Voici plusieurs nouvelles fonctionnalités de conception que cette nouvelle version du Concepteur de flux de travail indépendamment des versions antérieures du Concepteur de flux de travail :

-   Le Concepteur de flux de travail est créé à l’aide de Windows Presentation Foundation (WPF). Cela améliore l'expérience des concepteurs d'activités et les performances des workflows grands et complexes.

-   Les activités personnalisées sont maintenant conçues avec [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], à l'aide de XAML, et le modèle de programmation pour la création de concepteurs d'activités a été simplifié.

-   Une activité d'organigramme a été implémentée, afin de vous permettre de visualiser le flux du programme à l'aide du style de modélisation d'organigramme habituel.

-   Le Concepteur de flux de travail a un nouveau Concepteur de variables qui vous permet de déclarer et de limiter des variables dans votre flux de travail, les lier à des activités.

-   Dans Visual Studio 2010, le Concepteur de Workflow fournit des fonctionnalités IntelliSense complètes lors de la création d’expressions Visual Basic dans vos workflows .NET Framework 4.

-   L'expérience de débogage s'étend maintenant en XAML, ce qui vous permet de définir des points d'arrêt dans votre définition de workflow XAML et d'effectuer un pas à pas détaillé dans votre code XAML au moment de l'exécution, ce qui fournit une expérience comparable à celle que procure le code managé.

-   Réhébergement du Concepteur de flux de travail en dehors de Visual Studio est simplifié par rapport aux versions précédentes, ne nécessitant maintenant que quelques lignes de code.

-   La nouvelle <xref:System.Activities.Statements.Flowchart> activité et ses [organigramme](../workflow-designer/flowchart-activity-designer.md) vous permettent de visualiser votre flux de programme à l’aide de l’organigramme style de modélisation.

-   Les activités de messagerie ont été améliorées, ce qui vous permet d’écrire entièrement déclaratifs (sans code) les services Windows Communication Foundation (WCF).

-   Le **ajouter une référence de Service...**  fonctionnalité vous permet de générer automatiquement des activités qui accèdent aux services Web.