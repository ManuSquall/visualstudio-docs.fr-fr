---
title: Personnalisation de l’interface utilisateur Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 257f87aedf5d4337e81fb6f251cc8df07f4e577c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88041062"
---
# <a name="office-ui-customization"></a>Personnalisation de l’interface utilisateur Office
  Vous pouvez personnaliser l'interface utilisateur des applications Microsoft Office à l'aide des outils de développement Office dans Visual Studio. Cette rubrique répertorie les fonctionnalités de l’interface utilisateur que vous pouvez personnaliser, comme décrit dans les sections suivantes :

- [Comparaison des fonctionnalités de l’interface utilisateur](#Comparison)

- [Volets actions et volets de tâches personnalisés](#Actions)

- [Interface utilisateur du ruban personnalisée](#Ribbon)

- [Mode Backstage](#Backstage)

- [Zones de formulaire Outlook](#FormRegion)

- [Contrôles sur les documents](#Controls)

- [Menus contextuels](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> Comparaison des fonctionnalités de l’interface utilisateur
 Le tableau suivant compare les principales fonctionnalités de l'interface utilisateur que vous pouvez personnaliser dans les projets Microsoft Office.

|Fonctionnalité|Types de projet pris en charge|Applications Microsoft Office prises en charge|
|-------------|-----------------------------|---------------------------------------------|
|Volet Actions|Personnalisations au niveau du document|Excel<br /><br /> Word|
|Volets de tâches personnalisés|Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|Interface utilisateur du ruban personnalisée|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Mode Backstage|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Zones de formulaire Outlook|Compléments VSTO|Outlook|
|Contrôles dans des documents|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> Word|
|Menus contextuels|Personnalisations au niveau du document<br /><br /> Compléments VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> Volets actions et volets de tâches personnalisés
 Les volets de tâches sont des panneaux d'interface utilisateur généralement ancrés à l'un des côtés d'une fenêtre dans une application Microsoft Office. Presque toutes les applications Microsoft Office intègrent des volets de tâches, tels que le volet Aide dans Word.

 Les outils de développement Office dans Visual Studio offrent deux façons de personnaliser des volets de tâches :

- Vous pouvez ajouter un volet Actions à une personnalisation au niveau du document. Par défaut, ce volet s'affiche sur le côté droit de l'application, à droite du document. Il peut aussi s'afficher à gauche, en haut ou en bas du document.

- Vous pouvez ajouter un volet de tâches personnalisé à un complément VSTO. Les utilisateurs peuvent ancrer les volets de tâches personnalisés aux différents côtés de la fenêtre d’application ou les faire glisser n’importe où dans la fenêtre.

  Les volets Actions et les volets de tâches personnalisés fournissent des fonctionnalités en hébergeant divers contrôles qui facilitent l'exécution de certaines tâches, telles que la saisie de données. Par rapport à un groupe Ruban, les volets Actions et les volets de tâches personnalisés proposent une zone beaucoup plus grande pour inclure le texte et les contrôles.

  Pour plus d’informations sur les volets actions, consultez [vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md). Pour plus d’informations sur les volets de tâches personnalisés, consultez [volets de tâches personnalisés](../vsto/custom-task-panes.md).

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> Interface utilisateur du ruban personnalisée
 Vous pouvez personnaliser l'interface utilisateur du ruban pour exposer les fonctionnalités que vous ajoutez aux applications Office. Le ruban est une façon d'organiser les commandes associées (sous forme de contrôles) pour les retrouver plus facilement. Vous pouvez créer vos propres groupes et onglets de ruban pour permettre aux utilisateurs d'accéder aux fonctionnalités fournies dans votre solution. La plupart des fonctionnalités accessibles via les menus et les barres d'outils dans les versions antérieures de Microsoft Office System sont maintenant accessibles à partir du ruban.

 Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

## <a name="backstage-view"></a><a name="Backstage"></a> Mode Backstage
 Dans les applications Office, cliquez sur l’onglet **fichier** pour ouvrir le mode Backstage. Le mode Backstage fournit une interface utilisateur qui combine des actions et des tâches de niveau fichier, et remplace les fonctionnalités similaires disponibles via le bouton Microsoft Office dans Microsoft Office System version 2007. Ce mode est intégralement extensible à l'aide de XML.

 Visual Studio ne fournit pas de concepteur ni d'API pour personnaliser le mode Backstage. Toutefois, si vous ajoutez un élément **Ruban (XML)** à votre projet Office, vous pouvez ajouter du code XML au fichier XML du ruban pour personnaliser le mode Backstage. Pour plus d’informations sur les éléments **Ruban (XML)** , consultez [Ruban XML](../vsto/ribbon-xml.md).

 Pour plus d’informations sur la personnalisation du mode Backstage, consultez [Introduction au mode Backstage office 2010 pour les développeurs](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) et [Personnalisation du mode backstage d’Office 2010 pour les développeurs](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

## <a name="outlook-form-regions"></a><a name="FormRegion"></a> Zones de formulaire Outlook
 Utilisez des zones de formulaire pour ajouter des fonctionnalités personnalisées aux formulaires Microsoft Office Outlook standard. Vous pouvez créer des zones de formulaire qui étendent tout formulaire existant avec des champs ou contrôles supplémentaires. Si vous créez une zone de formulaire à l'aide des outils de développement Office dans Visual Studio, vous pouvez utiliser uniquement des contrôles Windows Forms dans cette zone de formulaire. Si vous importez une zone de formulaire conçue dans Outlook, vous pouvez alors utiliser des contrôles Outlook natifs uniquement.

 Vous pouvez créer des zones de formulaire qui occupent différents endroits de l'interface utilisateur d'Outlook. Par exemple, ces zones de formulaire adjacentes s'affichent en bas de la première page d'un formulaire et sont toutes réductibles. Vous pouvez aussi ajouter une zone de formulaire distincte qui s'affiche comme page de formulaire supplémentaire complète et peut apparaître sur tout formulaire standard ou personnalisé existant.

 Pour plus d’informations, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="controls-on-documents"></a><a name="Controls"></a> Contrôles sur les documents
 Vous pouvez ajouter divers contrôles aux documents Word et aux feuilles de calcul Excel. Par exemple, ajoutez un contrôle sélecteur de dates à un document pour permettre à l'utilisateur d'entrer des dates dans un format standard, ou placez un bouton dans une feuille de calcul pour envoyer des données vers une base de données.

 Quand vous développez un projet de niveau document pour Excel ou Word, vous pouvez utiliser le concepteur Visual Studio pour ajouter des contrôles au document ou au classeur dans votre projet au moment du design, ou les ajouter par programmation au moment de l'exécution. Quand vous développez des projets de complément VSTO pour Excel ou Word, vous pouvez ajouter des contrôles par programmation à n’importe quel document ou classeur ouvert au moment de l’exécution.

 Pour plus d’informations, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md) et [vue d’ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="shortcut-menus"></a><a name="Shortcut"></a> Menus contextuels
 Un menu contextuel s'affiche lorsque vous cliquez avec le bouton droit dans un document ou une fenêtre d'application. Vous pouvez définir un menu contextuel pour qu'il apparaisse quand un événement se produit (par exemple, quand un utilisateur clique avec le bouton droit sur un document, un classeur ou un contrôle hôte). Vous avez la possibilité d'ajouter divers contrôles ou commandes de menu à un menu contextuel, et créer des menus contextuels à l'aide de XML. Si vous ajoutez un élément **Ruban (XML)** à votre projet Office, vous pouvez ajouter du code XML au fichier XML du ruban pour créer des menus contextuels. Pour plus d’informations sur l’utilisation de XML pour créer des menus contextuels, consultez [Comment : ajouter des commandes à des menus contextuels](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Vue d’ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Volets des tâches personnalisés](../vsto/custom-task-panes.md)
- [Utiliser des contrôles WPF dans les solutions Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Comment : afficher les erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procédure pas à pas : collecter des données à l’aide d’un Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
