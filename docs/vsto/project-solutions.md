---
title: Solutions de projet
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
ms.openlocfilehash: f2158918aa6c2487719043abd797eb9d5e8f3f2e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551384"
---
# <a name="project-solutions"></a>Solutions de projet
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Project. Vous pouvez utiliser les compléments VSTO pour automatiser Project, étendre les fonctionnalités de Project ou personnaliser l’interface utilisateur de Project.

 Pour plus d’informations sur les compléments VSTO, consultez prise en main de la [programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md) et [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md). Si vous débutez avec la programmation avec Microsoft Office, consultez la page [prise en main &#40;du&#41;développement Office dans Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatiser le projet à l’aide du modèle objet Project
 Le modèle objet Project expose de nombreux types que vous pouvez utiliser pour automatiser Project. Ces types vous permettent d’écrire du code pour accomplir des tâches courantes telles que la création et la modification de tâches dans un projet par programmation.

 Pour accéder au modèle objet Project à partir d’un complément VSTO, utilisez le `Application` champ de la `ThisAddIn` classe dans votre projet. Le `Application` champ retourne un `Microsoft.Office.Interop.MsProject.Application` objet qui représente l’instance actuelle du projet. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

 Quand vous appelez le modèle objet Project, vous utilisez des types fournis dans l’assembly PIA (Primary Interop Assembly) pour Project. L’assembly PIA fait office de pont entre le code managé du complément VSTO et le modèle objet COM dans Project. Tous les types de l’assembly PIA Project sont définis dans l’espace de noms `Microsoft.Office.Interop.MSProject`. Pour plus d’informations sur les assemblys PIA, consultez [vue d’ensemble &#40;du&#41; développement des solutions Office VSTO](../vsto/office-solutions-development-overview-vsto.md) et [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Utiliser la documentation du modèle objet Project
 Pour obtenir des informations complètes sur le modèle objet Project, vous pouvez vous reporter à la référence du modèle objet Project VBA. La documentation de référence du modèle objet VBA présente le modèle objet Project tel qu’il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).

 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l’assembly PIA Project. Par exemple, l’objet de calendrier dans la documentation de référence du modèle objet `Microsoft.Office.Interop.MSProject.Calendar` VBA correspond au type dans l’assembly PIA du projet. Bien que la documentation de référence du modèle objet VBA fournisse des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code C# VBA de cette référence en Visual Basic ou visuel si vous souhaitez les utiliser dans un projet de complément VSTO de projet que vous créez à l’aide de à l’aide de Visual Studio.

> [!NOTE]
> À l’heure actuelle, il n’existe aucune documentation de référence pour l’assembly PIA Project.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Types d’infrastructure dans l’assembly PIA du projet
 Lors de l’écriture de code qui utilise l’assembly PIA Project, vous remarquerez peut-être de nombreux types qui ne sont pas décrits dans la référence VBA. Ces types supplémentaires aident à convertir des objets dans le modèle objet COM de Project en code managé. Ils ne sont pas censés être utilisés directement dans votre code.

 Pour plus d’informations, consultez [vue d’ensemble des classes et des interfaces dans les assemblys PIA (Primary Interop Assembly](http://go.microsoft.com/fwlink/?LinkId=189592)) d’Office.

## <a name="customize-the-user-interface-of-project"></a>Personnaliser l’interface utilisateur du projet
 Vous pouvez personnaliser l’interface utilisateur de Project de différentes façons.

|Tâche|Pour plus d'informations|
|----------|--------------------------|
|Ajouter des onglets personnalisés au ruban dans Project|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur de Project et d’autres applications de Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Créer votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Vue d’ensemble du &#40;développement des solutions Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Project 2010 et Project Server 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199016)
