---
title: Outlook (solutions)
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b27f874766853fb5239c96ec178233935484d1b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551489"
---
# <a name="outlook-solutions"></a>Outlook (solutions)
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des compléments VSTO pour Microsoft Office Outlook. Vous pouvez utiliser les compléments VSTO pour automatiser Outlook, étendre les fonctionnalités d'Outlook ou personnaliser l'interface utilisateur d'Outlook. Pour plus d’informations sur les compléments VSTO, consultez [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Créer un projet de complément VSTO Outlook
 Créez un projet Outlook à l'aide du modèle de projet **Complément Outlook** de la boîte de dialogue **Nouveau projet** . Ce modèle inclut les références d'assembly et les fichiers projet requis.

 Pour plus d’informations sur la création d’un projet de complément VSTO, consultez [procédure: Créer des projets Office dans Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio. Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Modèle de programmation de complément VSTO Outlook
 Lorsque vous créez un projet de complément VSTO Outlook, Visual Studio génère une classe, appelée `ThisAddIn`, qui est le fondement de votre solution. Cette classe fournit un point de départ pour l'écriture de votre code, et expose également le modèle objet d'Outlook à votre complément.

 Pour plus d’informations sur `ThisAddIn` la classe et les autres fonctionnalités que vous pouvez utiliser dans un complément VSTO, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatiser Outlook à l’aide du modèle objet Outlook
 Le modèle objet Outlook expose de nombreux types que vous pouvez utiliser pour automatiser Outlook. Ces types permettent d'écrire le code pour accomplir les tâches courantes :

- Créer et envoyer des messages électroniques par programmation.

- Envoyer de nouvelles demandes de réunion.

- Rechercher des éléments dans les dossiers Outlook.

  Pour plus d’informations, consultez [vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Personnaliser l’interface utilisateur d’une application Outlook

|Tâche|Pour plus d'informations|
|----------|--------------------------|
|Ajouter des onglets personnalisés au ruban d'un inspecteur Outlook.|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|
|Ajouter des groupes personnalisés à un onglet intégré d'un inspecteur Outlook.|[Guide pratique : Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)|
|Ajouter un volet des tâches personnalisé qui s'affiche dans un inspecteur Outlook|[Volets de tâches personnalisés](../vsto/custom-task-panes.md).|
|Ajouter une zone de formulaire qui étend ou remplace des formulaires Outlook existants.|[Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)|

 Pour plus d’informations sur la personnalisation de l’interface utilisateur d’Outlook et d’autres applications de Microsoft Office, consultez Personnalisation de l' [interface utilisateur Office](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble du modèle objet Outlook](../vsto/outlook-object-model-overview.md)|Fournit une vue d'ensemble des objets qui sont fournis par le modèle objet Outlook.|
|[Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)|Décrit les outils fournis par Visual Studio qui simplifient la conception, le développement et le débogage des zones de formulaire.|
|[Procédure pas à pas : Créer votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Explique comment créer un complément VSTO pour Microsoft Office Outlook.|
|[Outlook 2010 dans le développement Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Zone de MSDN Library où vous pouvez rechercher des articles et de la documentation de référence sur le développement de solutions Outlook (non spécifiques au développement d'Office à l'aide de Visual Studio).|
