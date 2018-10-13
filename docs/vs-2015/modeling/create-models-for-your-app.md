---
title: Créer des modèles pour votre application | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: eb7c2e0095d83ecbe21e6002f86c44682745341a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301897"
---
# <a name="create-models-for-your-app"></a>Créer des modèles pour votre application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les diagrammes de modélisation vous aident à comprendre, clarifier et communiquer vos idées concernant votre code et les besoins des utilisateurs que votre système logiciel doit prendre en charge. Par exemple, pour décrire et communiquer les besoins des utilisateurs, vous pouvez utiliser des diagrammes de cas d'usage, d'activités, de classe et de séquence UML (Unified Modeling Language). Pour décrire et communiquer les fonctionnalités de votre système, vous pouvez utiliser des diagrammes de composants, de classes, d'activités et de séquence UML.  
  
 Voir [Channel 9 Video : améliorer l’architecture par une modélisation de](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Vous pouvez créer les diagrammes UML suivants dans cette version :  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|---------------|  
|[Informations de référence sur les diagrammes d’activités UML](../modeling/uml-activity-diagrams-reference.md)|Flux de travail entre les actions et les participants dans un processus d'entreprise|  
|[Informations de référence sur les diagrammes de composants UML](../modeling/uml-component-diagrams-reference.md)|Composants d'un système, leurs interfaces, ports et relations|  
|[Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)|Types qui sont utilisés pour stocker et échanger des données dans le système et leurs relations|  
|[Informations de référence sur les diagrammes de séquence UML](../modeling/uml-sequence-diagrams-reference.md)|Séquences d'interactions entre des objets, des composants, des systèmes ou des acteurs|  
|[Informations de référence sur les diagrammes de cas d’usage UML](../modeling/uml-use-case-diagrams-reference.md)|Tâches et objectifs de l'utilisateur pris en charge par un système|  
  
 Pour connaître les versions de Visual Studio prennent en charge chaque type de diagramme, consultez [versions prises en charge pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Pour visualiser l'architecture d'un système ou de code existant, créez les diagrammes suivants :  
  
|**Diagramme**|**Éléments décrits**|  
|-----------------|---------------|  
|[Diagrammes de couche : recommandations](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Informations de référence sur les diagrammes de couche](../modeling/layer-diagrams-reference.md)|Architecture de haut niveau du système|  
|Cartes de code<br /><br /> [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)|Dépendances et autres relations dans le code existant|  
|Diagrammes de classes générés par du code<br /><br /> [Utilisation des diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md)|Types et leurs relations dans le code .NET|  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|**Rubrique**|**Task**|  
|---------------|--------------|  
|[Créer des projets et des diagrammes de modélisation UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Créer des modèles** et ajouter des diagrammes.|  
|[Modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md)|**Dessiner des diagrammes** pour modifier le modèle.|  
|[Définir des packages et des espaces de noms](../modeling/define-packages-and-namespaces.md)|**Créer des packages** pour diviser un modèle en unités qui fonctionnent sur différents membres d’équipe.|  
|[Générer du code à partir de diagrammes de classes UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Générer du code c# à partir de diagrammes de classes** pour démarrer votre implémentation.|  
|[Personnaliser votre modèle avec des profils et des stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Personnaliser les éléments de modèle** à l’aide de stéréotypes pour étendre les éléments de modèle UML standards à des fins spécifiques.|  
|[Lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md)|**Créer des liens entre éléments de modèle et les éléments de travail** pour vous aider à effectuer le suivi des tâches, les cas de test, les bogues, les spécifications, problèmes ou autres genres de travaux qui sont associés à des parties spécifiques de votre modèle.|  
|[Exporter des diagrammes en tant qu’images](../modeling/export-diagrams-as-images.md)|**Enregistrer votre modèle et les diagrammes** afin que vous pouvez les partager avec d’autres utilisateurs, y compris ceux qui n’utilisent pas [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|  
  
## <a name="related-tasks"></a>Tâches connexes  
  
|**Rubrique**|**Task**|  
|---------------|--------------|  
|[Visualiser du code](../modeling/visualize-code.md)|Créer des cartes de code et des diagrammes de couche pour mieux comprendre le code inconnu.|  
|[Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)|Utiliser des modèles pour clarifier et communiquer les besoins des utilisateurs.|  
|[Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|Utiliser des modèles pour décrire la structure globale et le comportement de votre système et pour vous assurer qu'il répond aux besoins des utilisateurs.|  
|[Valider votre système pendant le développement](../modeling/validate-your-system-during-development.md)|Assurez-vous que votre logiciel reste cohérent avec les besoins de vos utilisateurs et avec l'architecture globale de votre système.|  
|[Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)<br /><br /> [Utiliser des modèles dans le développement Agile](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)|Utiliser des modèles pour vous aider à comprendre et à modifier votre système lors de son développement.|  
|[Structurer votre solution de modélisation](../modeling/structure-your-modeling-solution.md)|Organiser les modèles dans un projet de grande ou moyenne taille.|  
  
## <a name="external-resources"></a>Ressources externes  
  
|**Catégorie**|**Links**|  
|------------------|---------------|  
|**Forums**|-   [Outils de visualisation et de modélisation Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling (outils DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|



