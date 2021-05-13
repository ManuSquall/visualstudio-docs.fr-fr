---
title: Prise en main de la programmation de compléments VSTO
description: Découvrez comment vous pouvez utiliser les compléments VSTO pour automatiser des applications Microsoft Office, étendre les fonctionnalités de l’application et personnaliser l’interface utilisateur de l’application.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848290"
---
# <a name="get-started-programming-vsto-add-ins"></a>Prise en main de la programmation de compléments VSTO
> [!IMPORTANT]
> VSTO s’appuie sur le [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Les compléments COM peuvent également être écrits avec l' .NET Framework. Impossible de créer des compléments Office avec [.net Core et .net 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five), les dernières versions de .net. Cela est dû au fait que .NET Core/. NET 5 + ne peut pas fonctionner conjointement avec .NET Framework dans le même processus et peut entraîner des échecs de chargement de complément. Vous pouvez continuer à utiliser .NET Framework pour écrire des compléments VSTO et COM pour Office. Microsoft ne mettra pas à jour VSTO ou la plateforme de complément COM pour utiliser .NET Core ou .NET 5 +. Vous pouvez tirer parti de .NET Core et de .NET 5 +, y compris ASP.NET Core, pour créer le côté serveur des [compléments Web Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins).

  Vous pouvez utiliser des compléments VSTO pour automatiser des applications Microsoft Office, étendre les fonctionnalités de l’application et personnaliser son interface utilisateur. Pour plus d’informations sur la façon dont les compléments VSTO sont comparés à d’autres types de solutions Office que vous pouvez créer à l’aide de Visual Studio, consultez [vue d’ensemble du développement des solutions office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Créer des projets de complément VSTO
 Créez des projets de complément VSTO en utilisant l’un des modèles de projet de complément VSTO dans la boîte de dialogue **nouveau projet** . Ces modèles comprennent les références d'assembly et les fichiers projet requis. Visual Studio fournit des modèles de projet de complément VSTO pour la plupart des applications dans Office.

 Pour plus d’informations sur la création d’un projet de complément VSTO, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Développer des projets de complément VSTO
 Quand vous créez un projet de complément VSTO, Visual Studio crée automatiquement un fichier de code *ThisAddIn. vb* (dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) ou *ThisAddIn. cs* (en C#). Ce fichier contient la `ThisAddIn` classe, qui fournit la base de votre complément VSTO. Vous pouvez utiliser des membres de cette classe pour exécuter le code quand le complément VSTO est chargé ou déchargé, pour accéder au modèle objet de l’application hôte, et pour étendre les fonctionnalités de l’application. Pour plus d’informations, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatiser des applications à l’aide des modèles objet
 Les modèles objet des applications Microsoft Office exposent de nombreux types avec lesquels vous pouvez programmer dans un complément VSTO. Vous pouvez utiliser ces types pour automatiser l'application. Par exemple, vous pouvez créer et envoyer par programme un message électronique dans Outlook ou encore ouvrir un document et ajouter du contenu dans Word. Pour plus d’informations sur l’accès au modèle objet de l’application hôte dans le code, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

 Pour plus d'informations sur les modèles objet d'applications Microsoft Office spécifiques, consultez les rubriques suivantes :

- [Vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)

- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)

- [Vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md)

- [Solutions InfoPath](../vsto/infopath-solutions.md)

- [Solutions PowerPoint](../vsto/powerpoint-solutions.md)

- [Solutions de projet](../vsto/project-solutions.md)

- [Vue d’ensemble du modèle objet Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personnaliser l’interface utilisateur des applications
 Il existe différentes façons de personnaliser l’interface utilisateur de l’application hôte à l’aide d’un complément VSTO :

- Pour Excel et Word, vous pouvez ajouter des contrôles managés aux documents. Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

- Vous pouvez personnaliser le ruban si l'application le prend en charge. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

- Vous pouvez créer un volet de tâches personnalisé si l’application le prend en charge. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

- Pour Outlook, vous pouvez créer une zone de formulaire personnalisée. Pour plus d’informations, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

- Pour toutes les applications Microsoft Office, vous pouvez afficher Windows Forms dans votre complément VSTO.

  Pour plus d’informations sur la personnalisation de l’interface utilisateur des applications Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Étapes suivantes
 Pour savoir comment créer des compléments VSTO, consultez les procédures pas à pas suivantes :

- [Procédure pas à pas : créer votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Procédure pas à pas : créer votre première Add-In VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Ces procédures pas à pas vous initient aux Outils de développement Office dans Visual Studio et au modèle de programmation pour les compléments VSTO.

  Pour obtenir la liste des rubriques qui vous guident lors de certaines tâches courantes dans les projets Office, consultez [tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)
