---
title: solutions InfoPath
description: Découvrez comment vous pouvez utiliser Visual Studio pour créer des compléments VSTO pour Microsoft InfoPath 2013 et InfoPath 2010.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3feab4a4b66ed2d6cf96fbccc8aaf1fb7de3bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962364"
---
# <a name="infopath-solutions"></a>solutions InfoPath
  Visual Studio fournit des modèles de projet à l’aide desquels vous pouvez créer des compléments VSTO pour Microsoft Office InfoPath 2013 et InfoPath 2010. InfoPath n’est pas disponible dans Office 2016.

> [!NOTE]
> Vous pouvez toujours créer un complément VSTO pour InfoPath même si vous avez installé Office 2016. Pour cela, installez simplement InfoPath 2013 ou Office 2013 côte à côte avec Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Les compléments VSTO pour InfoPath sont semblables aux compléments VSTO conçus pour les autres applications Microsoft Office. Ces types de solutions se composent d'un assembly chargé par l'application. L'utilisateur final peut accéder aux fonctionnalités de cet assembly quel que soit le formulaire ou le modèle de formulaire ouvert. Pour plus d’informations sur les compléments VSTO, consultez prise en main de la [programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Visual Studio 2015 n'inclut pas les projets de modèle de formulaire InfoPath qui étaient disponibles dans les versions antérieures de Visual Studio. Vous ne pouvez pas non plus utiliser Visual Studio 2015 pour ouvrir ou modifier un projet de modèle de formulaire InfoPath qui a été créé dans une version antérieure de Visual Studio. Toutefois, cela est possible en utilisant Visual Studio Tools pour Applications. Pour plus d’informations, consultez [utiliser des projets VSTO 2008 dans InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatiser InfoPath à l’aide d’un complément
 Pour accéder au modèle objet d’InfoPath à partir d’un complément VSTO Office créé à l’aide des outils de développement Office dans Visual Studio, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet <xref:Microsoft.Office.Interop.InfoPath.Application> qui représente l'instance actuelle d'InfoPath. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

 Quand vous appelez le modèle objet d’InfoPath à partir d’un complément VSTO, vous utilisez des types fournis dans l’assembly PIA (Primary Interop Assembly) pour InfoPath. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans InfoPath. Tous les types dans l'assembly PIA d'InfoPath sont définis dans l'espace de noms <xref:Microsoft.Office.Interop.InfoPath> . Pour plus d’informations sur l’assembly PIA d’InfoPath, consultez [à propos de l’assembly PIA (Primary Interop Assembly) Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly). Pour plus d’informations sur les assemblys PIA en général, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Personnaliser l’interface utilisateur d’InfoPath à l’aide d’un complément
 Lorsque vous créez un complément VSTO pour InfoPath, vous avez plusieurs options de personnalisation de l’interface utilisateur. Le tableau suivant répertorie certaines de ces options.

|Tâche|Informations supplémentaires|
|----------|--------------------------|
|Créer un volet des tâches personnalisé.|[Volets des tâches personnalisés](../vsto/custom-task-panes.md)|
|Ajouter des onglets personnalisés au ruban dans InfoPath|[Personnaliser un ruban pour InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur d’InfoPath et d’autres applications de Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Voir aussi
- [À propos de l’assembly PIA (Primary Interop Assembly) Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 dans le développement Office](/previous-versions/office/developer/office-2010/ff604966(v=office.14))