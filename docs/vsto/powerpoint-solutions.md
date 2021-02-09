---
title: Solutions PowerPoint
description: Découvrez que Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft PowerPoint.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4033c3fbae9aaefdc094d94d3a4ba70b67d40bf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891902"
---
# <a name="powerpoint-solutions"></a>Solutions PowerPoint
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office PowerPoint. Vous pouvez utiliser les compléments VSTO pour automatiser PowerPoint, étendre les fonctionnalités PowerPoint ou personnaliser l’interface utilisateur PowerPoint.

 Pour plus d’informations sur les compléments VSTO, consultez prise en main de la [programmation de compléments VSTO](getting-started-programming-vsto-add-ins.md) et [architecture des compléments VSTO](architecture-of-vsto-add-ins.md). Si vous débutez avec la programmation avec Microsoft Office, consultez [prise en main &#40;le développement Office dans Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatiser PowerPoint à l’aide du modèle objet PowerPoint
 Le modèle objet PowerPoint expose de nombreux types que vous pouvez utiliser pour automatiser PowerPoint. Ces types permettent d'écrire le code pour accomplir les tâches courantes :

- créer et mettre en forme les présentations par programmation ;

- ajouter ou supprimer des diapositives des présentations ;

- ajouter ou modifier des formes sur une diapositive.

  Pour accéder au modèle objet PowerPoint à partir d’un complément VSTO, utilisez le `Application` champ de la `ThisAddIn` classe dans votre projet. Le `Application` champ retourne un objet d' [application](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) qui représente l’instance actuelle de PowerPoint. Pour plus d’informations, consultez [compléments VSTO du programme](programming-vsto-add-ins.md).

  Quand vous appelez le modèle objet PowerPoint, vous utilisez des types fournis dans l'assembly PIA (Primary Interop Assembly) pour PowerPoint. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans PowerPoint. Tous les types dans l’assembly PIA (Primary Interop Assembly) PowerPoint sont définis dans l’espace de noms [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Pour plus d’informations sur les assemblys PIA, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md) et [assemblys PIA (Primary Interop Assembly) Office](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Utiliser la documentation du modèle objet PowerPoint
 Pour obtenir des informations complètes sur le modèle objet PowerPoint, vous pouvez vous reporter à la documentation de référence de l'assembly PIA (Primary Interop Assembly) PowerPoint et à la documentation de référence du modèle objet VBA.

### <a name="primary-interop-assembly-reference"></a>Référence d’assembly PIA (Primary Interop Assembly)
 La documentation de référence de l'assembly PIA PowerPoint décrit les types de l'assembly PIA pour PowerPoint. Cette documentation est disponible à partir de l’emplacement suivant : référence de l' [assembly PIA PowerPoint 2010](office-primary-interop-assemblies.md).

 Pour plus d’informations sur la conception de l’assembly PIA PowerPoint, telles que les différences entre les classes et les interfaces dans l’assembly PIA et le mode d’implémentation des événements dans l’assembly PIA, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA (Primary Interop Assembly](/previous-versions/office/developer/office-2010/ff759900(v=office.14))) d’Office.

### <a name="vba-object-model-reference"></a>Référence du modèle objet VBA
 La documentation de référence du modèle objet VBA présente le modèle objet PowerPoint tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet PowerPoint 2010](/office/vba/api/overview/PowerPoint/object-model).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA PowerPoint. Par exemple, l’objet Presentation dans la documentation de référence du modèle objet VBA correspond au type de [Présentation](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) dans l’assembly PIA PowerPoint. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans cette documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément VSTO PowerPoint créé à l’aide de Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personnaliser l’interface utilisateur de PowerPoint
 Vous pouvez modifier l'interface utilisateur de PowerPoint comme suit.

|Tâche|Informations supplémentaires|
|----------|--------------------------|
|Créer un volet des tâches personnalisé.|[Volets des tâches personnalisés](custom-task-panes.md)|
|Ajouter des onglets personnalisés au ruban.|[Vue d’ensemble du ruban](ribbon-overview.md)|
|Ajouter des groupes personnalisés à un onglet intégré du ruban.|[Comment : personnaliser un onglet intégré](how-to-customize-a-built-in-tab.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur de PowerPoint et d’autres applications de Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](office-ui-customization.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : créer votre premier complément VSTO pour PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Prise en main de la programmation de compléments VSTO](getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](architecture-of-vsto-add-ins.md)
- [Comment : créer des projets Office dans Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Programmer les compléments VSTO](programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](writing-code-in-office-solutions.md)
- [Assemblys PIA (Primary Interop Assembly) Office](office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](office-ui-customization.md)
- [PowerPoint 2010 dans le développement Office](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
