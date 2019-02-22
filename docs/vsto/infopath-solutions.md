---
title: solutions InfoPath
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 674050711e69ae97c7e1faa361122bee0d755ae7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621147"
---
# <a name="infopath-solutions"></a>solutions InfoPath
  Visual Studio fournit des modèles de projet à l’aide desquels vous pouvez créer des compléments VSTO pour Microsoft Office InfoPath 2013 et InfoPath 2010. InfoPath n’est pas disponible dans Office 2016.

> [!NOTE]
>  Vous pouvez toujours créer un composant logiciel complément VSTO pour InfoPath même si vous avez installé Office 2016. Pour cela, installez simplement InfoPath 2013 ou Office 2013 côte à côte avec Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

> [!NOTE]
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.

 Les compléments VSTO pour InfoPath sont semblables aux compléments VSTO conçus pour les autres applications Microsoft Office. Ces types de solutions se composent d'un assembly chargé par l'application. L'utilisateur final peut accéder aux fonctionnalités de cet assembly quel que soit le formulaire ou le modèle de formulaire ouvert. Pour plus d’informations sur les Compléments VSTO, consultez [commencer à programmer des Compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
>  Visual Studio 2015 n'inclut pas les projets de modèle de formulaire InfoPath qui étaient disponibles dans les versions antérieures de Visual Studio. Vous ne pouvez pas non plus utiliser Visual Studio 2015 pour ouvrir ou modifier un projet de modèle de formulaire InfoPath qui a été créé dans une version antérieure de Visual Studio. Toutefois, cela est possible en utilisant Visual Studio Tools pour Applications. Pour plus d’informations, consultez [fonctionnent avec les projets VSTO 2008 dans InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).

## <a name="automate-infopath-by-using-an-add-in"></a>Automatiser InfoPath en utilisant un complément
 Pour accéder au modèle objet d’InfoPath à partir d’un complément VSTO Office créé à l’aide des outils de développement Office dans Visual Studio, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.InfoPath.Application> qui représente l'instance actuelle d'InfoPath. Pour plus d’informations, consultez [programme VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Lorsque vous appelez le modèle objet d’InfoPath à partir d’un complément, VSTO, vous utilisez des types fournis dans l’assembly PIA pour InfoPath. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans InfoPath. Tous les types dans l'assembly PIA d'InfoPath sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.InfoPath> . Pour plus d’informations sur l’assembly PIA d’InfoPath, consultez [assembly PIA sur Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Pour plus d’informations sur les assemblys PIA en général, consultez [présentation du développement de solutions Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Personnaliser l’interface utilisateur d’InfoPath à l’aide un complément
 Lorsque vous créez un complément, VSTO pour InfoPath, vous avez plusieurs options de personnalisation de l’interface utilisateur différentes. Le tableau suivant répertorie certaines de ces options.

|Tâche|Pour plus d'informations|
|----------|--------------------------|
|Créer un volet des tâches personnalisé.|[Volets Office personnalisés](../vsto/custom-task-panes.md)|
|Ajouter des onglets personnalisés au ruban dans InfoPath|[Personnaliser un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur d’InfoPath et d’autres applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Voir aussi
- [À propos de l’assembly PIA de Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)
- [Commencer à programmer des Compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199012)
