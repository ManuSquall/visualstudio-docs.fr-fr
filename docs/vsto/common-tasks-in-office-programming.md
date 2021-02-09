---
title: Tâches courantes dans la programmation Office
description: Découvrez comment programmer des données dans une personnalisation au niveau du document sans avoir à utiliser le modèle objet de Microsoft Office Word ou Office Excel.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 67b09d3881dcde1d404b7ff0c1096ced1ecb50ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910608"
---
# <a name="common-tasks-in-office-programming"></a>Tâches courantes dans la programmation Office
  Cette rubrique est conçue pour vous aider à trouver les réponses aux catégories suivantes de questions courantes sur la programmation de solutions Office à l’aide de Visual Studio.

- [Tâches d’installation et tâches générales](#projects).

- [Tâches de personnalisation de l’interface utilisateur](#ui).

- [Tâches d’automatisation d’Excel](#excel).

- [Tâches d’automatisation de Word](#word).

- [Tâches relatives aux données](#data).

- [Tâches de gestion des documents côté serveur](#server).

- [Tâches de sécurité](#security).

- [Tâches de déploiement](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Tâches d’installation et tâches générales

- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Comment : mettre à niveau des solutions Office](/previous-versions/4bez6837(v=vs.140)).

- [Comment : installer les assemblys PIA (Primary Interop Assembly) d’Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Comment : cibler des applications Office via des assemblys PIA (Primary Interop Assembly](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)).

- [Comment : créer des gestionnaires d’événements dans les projets Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Comment : ouvrir des solutions Office sans exécuter de code](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Comment : configurer les informations de configuration d’une solution Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Comment : afficher les erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Tâches de personnalisation de l’interface utilisateur

### <a name="controls-on-documents-and-worksheets"></a>Contrôles sur des documents et des feuilles de calcul

- [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Comment : ajouter des contrôles ListObject à des feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Volets des tâches dans les personnalisations au niveau du document

- [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Volets des tâches dans les compléments VSTO

- [Comment : ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Personnalisations du ruban

- [Comment : commencer à personnaliser le ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Comment : modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md).

- [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Guide pratique pour exporter un ruban à partir du Concepteur de ruban vers l’élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Zones de formulaire Outlook

- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menus personnalisés

- [Comment : ajouter des commandes à des menus contextuels](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Tâches d’automatisation d’Excel

- [Comment : afficher une chaîne dans une cellule de feuille de calcul par programmation](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Comment : créer des classeurs par programmation](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Comment : ouvrir des classeurs par programmation](../vsto/how-to-programmatically-open-workbooks.md).

- [Comment : enregistrer des classeurs par programmation](../vsto/how-to-programmatically-save-workbooks.md).

- [Comment : fermer des classeurs par programmation](../vsto/how-to-programmatically-close-workbooks.md).

- [Comment : ajouter des feuilles de calcul à des classeurs par programmation](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Comment : masquer des feuilles de calcul par programmation](../vsto/how-to-programmatically-hide-worksheets.md).

- [Comment : déplacer des feuilles de calcul dans des classeurs par programmation](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Comment : protéger des classeurs par programmation](../vsto/how-to-programmatically-protect-workbooks.md).

- [Comment : faire référence à des plages de feuille de calcul dans le code par programmation](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Comment : appliquer des styles à des plages dans des classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Comment : modifier la mise en forme des lignes de feuille de calcul contenant des cellules sélectionnées par programmation](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Comment : Rechercher du texte dans les plages de la feuille de calcul par programmation](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Comment : imprimer des feuilles de calcul par programmation](../vsto/how-to-programmatically-print-worksheets.md).

- [Comment : exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Comment : trier des données par programmation dans des feuilles de calcul](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Tâches d’automatisation de Word

- [Comment : créer des documents par programmation](../vsto/how-to-programmatically-create-new-documents.md).

- [Comment : ouvrir des documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md).

- [Comment : enregistrer des documents par programmation](../vsto/how-to-programmatically-save-documents.md).

- [Comment : fermer des documents par programmation](../vsto/how-to-programmatically-close-documents.md).

- [Comment : insérer du texte dans des documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Comment : définir et sélectionner des plages dans les documents par programmation](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Comment : réinitialiser des plages dans les documents Word par programmation](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Comment : mettre en forme du texte dans des documents par programmation](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Comment : ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Comment : mettre à jour le texte d’un signet par programmation](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Comment : Rechercher et remplacer du texte dans des documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Comment : imprimer des documents par programmation](../vsto/how-to-programmatically-print-documents.md).

- [Comment : créer des tableaux Word par programmation](../vsto/how-to-programmatically-create-word-tables.md).

- [Comment : ajouter des lignes et des colonnes à des tableaux Word par programmation](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Comment : compter des caractères dans les documents par programmation](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Tâches de données

### <a name="data-bound-controls"></a>Contrôles liés aux données

- [Comment : remplir des feuilles de calcul avec des données d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Comment : remplir des documents avec des données de services](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Comment : remplir des documents avec des données de services](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Données mises en cache dans les solutions au niveau du document

- [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Données XML personnalisées

- [Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Comment : ajouter des parties XML personnalisées à des documents à l’aide des compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Tâches de gestion des documents côté serveur

- [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Comment : attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Tâches de sécurité

- [Comment : signer des solutions Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Tâches de déploiement

- [Comment : publier une solution Office à l’aide de ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Comment : publier une solution Office au niveau du document sur un serveur SharePoint à l’aide de ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Comment : installer une solution Office ClickOnce](/previous-versions/bb608592(v=vs.110)).

- [Procédure : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](/previous-versions/bb608608(v=vs.110)).

- [Comment : préparer IIS pour le déploiement de solutions Office](/previous-versions/bb608629(v=vs.110)).

- [Comment : mettre à jour les solutions Office déployées](/previous-versions/bb157871(v=vs.110)).

- [Comment : modifier le chemin d’installation d’une solution Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Voir aussi
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md)
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)