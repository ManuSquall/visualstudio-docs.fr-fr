---
title: Solutions Visio
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985506"
---
# <a name="visio-solutions"></a>Solutions Visio
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Visio. Vous pouvez utiliser les compléments VSTO pour automatiser Visio, étendre les fonctionnalités Visio ou personnaliser l'interface utilisateur de Visio.

 Pour plus d’informations sur les compléments VSTO, consultez prise en main de la [programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez avec la programmation avec Microsoft Office, consultez la page [prise en main &#40;du&#41;développement Office dans Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets de compléments VSTO pour Visio 2010. Pour plus d’informations, consultez [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatiser Visio à l’aide du modèle objet Visio
 Le modèle objet Visio expose de nombreuses classes que vous pouvez utiliser pour automatiser Visio afin de créer des diagrammes pour les organigrammes, diagrammes de flux, chronologies de projet, réseaux de tâches, espaces de bureau, etc. L'API vous permet d'écrire du code pour accomplir les tâches courantes :

- Élaborer et positionner des formes et du texte dans les diagrammes.

- Gérer le comportement des formes en fonction de la logique métier et des entrées d'utilisateur.

- Contrôler la visualisation des diagrammes, comme l'affichage panoramique et le zoom.

- Personnaliser l'interface utilisateur de l'application.

- Importer des données externes dans Visio, les lier aux formes et les afficher graphiquement dans une page.

  Vous pouvez afficher des procédures pas à pas et des exemples de code pour utiliser le modèle objet de Visio pour travailler avec des documents et des formes dans [utiliser des documents Visio](../vsto/working-with-visio-documents.md) et [travailler avec des formes Visio](../vsto/working-with-visio-shapes.md).

  Pour accéder au modèle objet Visio à partir d'un complément VSTO, utilisez le champ `Application` de la classe `ThisAddIn` dans votre projet. Le champ `Application` retourne un objet `Microsoft.Office.Interop.Visio.Application` qui représente l'instance actuelle de Visio. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

  Quand vous appelez le modèle objet Visio, vous utilisez des types fournis dans l'assembly PIA (Primary Interop Assembly) pour Visio. L'assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Visio. Tous les types figurant dans l'assembly PIA de Visio sont définis dans l'espace de noms `Microsoft.Office.Interop.Visio`. Pour plus d’informations sur les assemblys PIA, consultez [vue d’ensemble &#40;du&#41; développement des solutions Office VSTO](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Vue d’ensemble du modèle objet Visio
 Vous trouverez une vue d’ensemble du modèle objet Visio à la page [vue d’ensemble du modèle objet](../vsto/visio-object-model-overview.md)Visio, qui comprend des liens vers la référence du modèle objet Visio et les kits de développement logiciel (SDK).

## <a name="customize-the-user-interface-of-visio"></a>Personnaliser l’interface utilisateur de Visio
 L'interface utilisateur de Visio inclut les options de personnalisation suivantes.

|Tâche|Pour plus d'informations|
|----------|--------------------------|
|Personnaliser le ruban|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|

 Pour plus d'informations sur la personnalisation de l'interface utilisateur de Visio, consultez la documentation de référence sur VBA pour la classe [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Voir aussi
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du &#40;développement des solutions Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 dans le développement Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
