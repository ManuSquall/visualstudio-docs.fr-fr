---
title: Solutions Visio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 248fa3051a3d639798f37270dc7957a759e20d6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941982"
---
# <a name="visio-solutions"></a>Solutions Visio
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Visio. Vous pouvez utiliser les compléments VSTO pour automatiser Visio, étendre les fonctionnalités Visio ou personnaliser l'interface utilisateur de Visio.  
  
 Pour plus d’informations sur les Compléments VSTO, consultez [commencer à programmer des Compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Si vous êtes novice en programmation avec Microsoft Office, consultez [prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour Visio 2010. Pour plus d’informations, consultez [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatisation de Visio à l’aide du modèle objet Visio  
 Le modèle objet Visio expose de nombreuses classes que vous pouvez utiliser pour automatiser Visio afin de créer des diagrammes pour les organigrammes, diagrammes de flux, chronologies de projet, réseaux de tâches, espaces de bureau, etc. L'API vous permet d'écrire du code pour accomplir les tâches courantes :  
  
- Élaborer et positionner des formes et du texte dans les diagrammes.  
  
- Gérer le comportement des formes en fonction de la logique métier et des entrées d'utilisateur.  
  
- Contrôler la visualisation des diagrammes, comme l'affichage panoramique et le zoom.  
  
- Personnaliser l'interface utilisateur de l'application.  
  
- Importer des données externes dans Visio, les lier aux formes et les afficher graphiquement dans une page.  
  
  Vous pouvez visualiser des procédures pas à pas et exemples de code pour l’aide du modèle objet de Visio pour travailler avec des documents et des formes dans [travailler avec des documents Visio](../vsto/working-with-visio-documents.md) et [fonctionne avec les formes Visio](../vsto/working-with-visio-shapes.md).  
  
  Pour accéder au modèle objet Visio à partir d'un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet `Microsoft.Office.Interop.Visio.Application` qui représente l'instance actuelle de Visio. Pour plus d’informations, consultez [programme VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
  Quand vous appelez le modèle objet Visio, vous utilisez des types fournis dans l'assembly PIA (Primary Interop Assembly) pour Visio. L'assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Visio. Tous les types figurant dans l'assembly PIA de Visio sont définis dans l'espace de noms `Microsoft.Office.Interop.Visio`. Pour plus d’informations sur les assemblys PIA, consultez [présentation du développement de solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Présentation du modèle objet de Visio  
 Vous trouverez une vue d’ensemble du modèle objet Visio dans [présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md), qui inclut des liens vers la référence du modèle objet Visio et les kits de développement.  
  
## <a name="customize-the-user-interface-of-visio"></a>Personnaliser l’interface utilisateur de Visio  
 L'interface utilisateur de Visio inclut les options de personnalisation suivantes.  
  
|Tâche|Pour plus d'informations|  
|----------|--------------------------|  
|Personnaliser le ruban|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|  
  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur de Visio, consultez la documentation de référence sur VBA pour la classe [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) .  
  
## <a name="see-also"></a>Voir aussi  
 [Commencer à programmer des Compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)   
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  