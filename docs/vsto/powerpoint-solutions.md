---
title: Solutions PowerPoint
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 70968682a8221b88859fd561c9f678aced2911b9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551474"
---
# <a name="powerpoint-solutions"></a>Solutions PowerPoint
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office PowerPoint. Vous pouvez utiliser les compléments VSTO pour automatiser PowerPoint, étendre les fonctionnalités PowerPoint ou personnaliser l’interface utilisateur PowerPoint.

 Pour plus d’informations sur les compléments VSTO, consultez prise en main de la [programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez avec la programmation avec Microsoft Office, consultez la page [prise en main &#40;du&#41;développement Office dans Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, [consultez Comment faire: Créer un complément pour Microsoft PowerPoint ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatiser PowerPoint à l’aide du modèle objet PowerPoint
 Le modèle objet PowerPoint expose de nombreux types que vous pouvez utiliser pour automatiser PowerPoint. Ces types permettent d'écrire le code pour accomplir les tâches courantes :

- créer et mettre en forme les présentations par programmation ;

- ajouter ou supprimer des diapositives des présentations ;

- ajouter ou modifier des formes sur une diapositive.

  Pour accéder au modèle objet PowerPoint à partir d’un complément VSTO, utilisez le `Application` champ de la `ThisAddIn` classe dans votre projet. Le `Application` champ retourne un objet d' [application](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) qui représente l’instance actuelle de PowerPoint. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

  Quand vous appelez le modèle objet PowerPoint, vous utilisez des types fournis dans l'assembly PIA (Primary Interop Assembly) pour PowerPoint. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans PowerPoint. Tous les types dans l’assembly PIA (Primary Interop Assembly) PowerPoint sont définis dans l’espace de noms [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Pour plus d’informations sur les assemblys PIA, consultez [vue d’ensemble &#40;du&#41; développement des solutions Office VSTO](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

## <a name="WordOMDocumentation"></a>Utiliser la documentation du modèle objet PowerPoint
 Pour obtenir des informations complètes sur le modèle objet PowerPoint, vous pouvez vous reporter à la documentation de référence de l'assembly PIA (Primary Interop Assembly) PowerPoint et à la documentation de référence du modèle objet VBA.

### <a name="primary-interop-assembly-reference"></a>Référence d’assembly PIA (Primary Interop Assembly)
 La documentation de référence de l'assembly PIA PowerPoint décrit les types de l'assembly PIA pour PowerPoint. Cette documentation est disponible à partir de l’emplacement suivant: [Référence de l’assembly PIA PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Pour plus d’informations sur la conception de l’assembly PIA PowerPoint, telles que les différences entre les classes et les interfaces dans l’assembly PIA et le mode d’implémentation des événements dans l’assembly PIA, consultez [vue d’ensemble des classes et interfaces dans les assemblys PIA (Primary Interop Assembly](http://go.microsoft.com/fwlink/?LinkId=199885)) d’Office.

### <a name="vba-object-model-reference"></a>Référence du modèle objet VBA
 La documentation de référence du modèle objet VBA présente le modèle objet PowerPoint tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA PowerPoint. Par exemple, l’objet Presentation dans la documentation de référence du modèle objet VBA correspond au type de [Présentation](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) dans l’assembly PIA PowerPoint. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans cette documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément VSTO PowerPoint créé à l’aide de Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personnaliser l’interface utilisateur de PowerPoint
 Vous pouvez modifier l'interface utilisateur de PowerPoint comme suit.

|Tâche|Pour plus d'informations|
|----------|--------------------------|
|Créer un volet des tâches personnalisé.|[Volets des tâches personnalisés](../vsto/custom-task-panes.md)|
|Ajouter des onglets personnalisés au ruban.|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|
|Ajouter des groupes personnalisés à un onglet intégré du ruban.|[Guide pratique : Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur de PowerPoint et d’autres applications de Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Créer votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du &#40;développement des solutions Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199015)
