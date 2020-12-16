---
title: Solutions de projet
description: Découvrez comment vous pouvez utiliser les compléments VSTO pour automatiser Project, étendre les fonctionnalités du projet ou personnaliser l’interface utilisateur du projet.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c44e1208daaef11cb7fd9bd22e3e3ae574ca610d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527509"
---
# <a name="project-solutions"></a>Solutions de projet
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Project. Vous pouvez utiliser les compléments VSTO pour automatiser Project, étendre les fonctionnalités de Project ou personnaliser l’interface utilisateur de Project.

 Pour plus d’informations sur les compléments VSTO, consultez prise en main de la [programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez avec la programmation avec Microsoft Office, consultez [prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatiser le projet à l’aide du modèle objet Project
 Le modèle objet Project expose de nombreux types que vous pouvez utiliser pour automatiser Project. Ces types vous permettent d’écrire du code pour accomplir des tâches courantes telles que la création et la modification de tâches dans un projet par programmation.

 Pour accéder au modèle objet Project à partir d’un complément VSTO, utilisez le `Application` champ de la `ThisAddIn` classe dans votre projet. Le `Application` champ retourne un `Microsoft.Office.Interop.MsProject.Application` objet qui représente l’instance actuelle du projet. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

 Quand vous appelez le modèle objet Project, vous utilisez des types fournis dans l’assembly PIA (Primary Interop Assembly) pour Project. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Project. Tous les types de l’assembly PIA Project sont définis dans l’espace de noms `Microsoft.Office.Interop.MSProject`. Pour plus d’informations sur les assemblys PIA, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Utiliser la documentation du modèle objet Project
 Pour obtenir des informations complètes sur le modèle objet Project, vous pouvez vous reporter à la référence du modèle objet Project VBA. La documentation de référence du modèle objet VBA présente le modèle objet Project tel qu’il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet de projet](/office/vba/api/project.object).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l’assembly PIA Project. Par exemple, l’objet de calendrier dans la documentation de référence du modèle objet VBA correspond au `Microsoft.Office.Interop.MSProject.Calendar` type dans l’assembly PIA du projet. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA de cette référence en Visual Basic ou Visual C# si vous souhaitez les utiliser dans un projet de complément VSTO Project que vous créez à l’aide de Visual Studio.

> [!NOTE]
> À l’heure actuelle, il n’existe aucune documentation de référence pour l’assembly PIA Project.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Types d’infrastructure dans l’assembly PIA du projet
 Lors de l’écriture de code qui utilise l’assembly PIA Project, vous remarquerez peut-être de nombreux types qui ne sont pas décrits dans la référence VBA. Ces types supplémentaires aident à convertir des objets dans le modèle objet COM de Project en code managé. Ils ne sont pas censés être utilisés directement dans votre code.

 Pour plus d’informations, consultez [vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly](/previous-versions/office/office-12/ms247299(v=office.12))) d’Office.

## <a name="customize-the-user-interface-of-project"></a>Personnaliser l’interface utilisateur du projet
 Vous pouvez personnaliser l’interface utilisateur de Project de différentes façons.

|Tâche|Informations supplémentaires|
|----------|--------------------------|
|Ajouter des onglets personnalisés au ruban dans Project|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur de Project et d’autres applications de Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : créer votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Project 2010 et Project Server 2010 dans le développement Office](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
