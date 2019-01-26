---
title: Commencer à programmer des Compléments VSTO
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b7827f76703964d76b8a9f217dd781c3f85be6db
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874428"
---
# <a name="get-started-programming-vsto-add-ins"></a>Commencer à programmer des Compléments VSTO
  Vous pouvez utiliser des compléments VSTO pour automatiser des applications Microsoft Office, étendre les fonctionnalités de l’application et personnaliser son interface utilisateur. Pour plus d’informations sur les différences de compléments VSTO à d’autres types de solutions Office que vous pouvez créer à l’aide de Visual Studio, consultez [présentation du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Créer des projets de complément VSTO  
 Créer des projets de complément VSTO en utilisant l’un des modèles de projet à VSTO Add-in dans le **nouveau projet** boîte de dialogue. Ces modèles comprennent les références d'assembly et les fichiers projet requis. Visual Studio fournit des modèles de projet de complément VSTO pour la plupart des applications dans Office.  
  
 Pour plus d’informations sur la création d’un projet de complément VSTO, consultez [Comment : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Développez des projets de complément VSTO  
 Lorsque vous créez un projet de complément VSTO, Visual Studio crée automatiquement un *ThisAddIn.vb* (dans [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ou *ThisAddIn.cs* (en c#) le fichier de code. Ce fichier contient la `ThisAddIn` classe, qui fournit la base de votre complément, VSTO. Vous pouvez utiliser des membres de cette classe pour exécuter le code quand le complément VSTO est chargé ou déchargé, pour accéder au modèle objet de l’application hôte, et pour étendre les fonctionnalités de l’application. Pour plus d’informations, consultez [programme VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatiser des applications en utilisant les modèles d’objet  
 Les modèles objet des applications Microsoft Office exposent de nombreux types avec lesquels vous pouvez programmer dans un complément VSTO. Vous pouvez utiliser ces types pour automatiser l'application. Par exemple, vous pouvez créer et envoyer par programme un message électronique dans Outlook ou encore ouvrir un document et ajouter du contenu dans Word. Pour plus d’informations sur la façon d’accéder au modèle objet de l’application hôte dans le code, consultez [programme VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Pour plus d'informations sur les modèles objet d'applications Microsoft Office spécifiques, consultez les rubriques suivantes :  
  
-   [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)  
  
-   [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)  
  
-   [Vue d’ensemble du modèle d’objet Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Solutions InfoPath](../vsto/infopath-solutions.md)  
  
-   [Solutions PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Solutions Project](../vsto/project-solutions.md)  
  
-   [Présentation du modèle objet de Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Personnaliser l’interface utilisateur des applications  
 Il existe différentes façons de personnaliser l’interface utilisateur de l’application hôte à l’aide un VSTO Add-in :  
  
- Pour Excel et Word, vous pouvez ajouter des contrôles managés aux documents. Pour plus d’informations, consultez [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
- Vous pouvez personnaliser le ruban si l'application le prend en charge. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
- Vous pouvez créer un volet de tâches personnalisé si l’application le prend en charge. Pour plus d’informations, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
- Pour Outlook, vous pouvez créer une zone de formulaire personnalisée. Pour plus d’informations, consultez [zones de formulaire Outlook créer](../vsto/creating-outlook-form-regions.md).  
  
- Pour toutes les applications Microsoft Office, vous pouvez afficher Windows Forms dans votre complément VSTO.  
  
  Pour plus d’informations sur la personnalisation de l’interface utilisateur des applications Microsoft Office, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour savoir comment créer des compléments VSTO, consultez les procédures pas à pas suivantes :  
  
- [Procédure pas à pas : Créer votre premier complément pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [Procédure pas à pas : Créer votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [Procédure pas à pas : Créer votre premier complément pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [Procédure pas à pas : Créer votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [Procédure pas à pas : Créer votre premier complément pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
  Ces procédures pas à pas vous initient aux Outils de développement Office dans Visual Studio et au modèle de programmation pour les compléments VSTO.  
  
  Pour obtenir la liste des rubriques qui vous guident dans certaines des tâches courantes dans les projets Office, consultez [tâches courantes dans la programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Programmer des Compléments VSTO](../vsto/programming-vsto-add-ins.md)  
