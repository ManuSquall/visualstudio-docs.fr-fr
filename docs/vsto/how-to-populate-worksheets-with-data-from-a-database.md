---
title: 'Comment : remplir des feuilles de calcul avec des données d’une base de données'
description: Découvrez comment vous pouvez utiliser les données d’un objet dans votre solution, et comment vous pouvez utiliser des contrôles de Windows Forms pour afficher les données dans une feuille de calcul.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 66f37a1639cb6a86f107d9372704d5c8364c6a18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918563"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Comment : remplir des feuilles de calcul avec des données d’une base de données

Vous pouvez accéder aux données des projets Office au niveau du document de la même façon que vous accédez aux données des projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel qui ont été améliorés avec des événements et une fonctionnalité de liaison de données. Pour plus d’informations, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

L'exemple suivant montre comment ajouter des contrôles liés aux données dans les projets au niveau du document à l'aide d'un concepteur. Pour obtenir un exemple d’ajout de contrôles liés aux données dans des projets au niveau de l’application au moment de l’exécution, consultez [procédure pas à pas : liaison de données complexe dans un projet de complément VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Ajouter un contrôle lié aux données à une feuille de calcul au moment du design

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Pour remplir une feuille de calcul avec des données d’une base de données

1. Ouvrez un projet au niveau du document Excel dans Visual Studio, avec la feuille de calcul ouverte dans le concepteur.

2. Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. Faites glisser le champ ou la table de votre choix de la fenêtre **sources de données** vers votre feuille de calcul.

L’un des contrôles suivants est créé sur la feuille de calcul :

- Si vous faites glisser un champ, un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle est créé sur la feuille de calcul. Pour plus d’informations, consultez [NamedRange, contrôle](../vsto/namedrange-control.md).

- Si vous faites glisser une table, un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle est créé sur la feuille de calcul. Pour plus d’informations, consultez [ListObject Control](../vsto/listobject-control.md).

Vous pouvez ajouter un contrôle différent en sélectionnant la table ou le champ dans la fenêtre **sources de données** , puis en choisissant un autre contrôle dans la liste déroulante.

## <a name="objects-in-the-project"></a>Objets du projet

Outre le contrôle, les objets de données suivants sont automatiquement ajoutés à votre projet :

- Un dataset typé qui encapsule les tables de données auxquelles vous êtes connecté dans la base de données. Pour plus d’informations, consultez [outils de jeu de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au dataset typé. Pour plus d’informations, consultez [vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter qui connecte le DataSet typé à la base de données. Pour plus d’informations, consultez [vue d’ensemble de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- TableAdapterManager, qui est utilisé pour coordonner les adaptateurs de table dans le DataSet afin d’activer les mises à jour hiérarchiques. Pour plus d’informations, consultez [mise à jour hiérarchique](../data-tools/hierarchical-update.md) et [référence de TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Lorsque vous exécutez le projet, le contrôle affiche le premier enregistrement de la source de données. Vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> pour permettre aux utilisateurs de faire défiler les enregistrements.

### <a name="to-scroll-through-the-records"></a>Pour faire défiler les enregistrements

- Utilisez les méthodes <xref:System.Windows.Forms.BindingSource> telles que <xref:System.Windows.Forms.BindingSource.MoveNext%2A> et <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Pour plus d’informations sur la façon d’envoyer des mises à jour au DataSet typé et à la base de données, consultez [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Voir aussi

- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Comment : remplir des documents avec des données de services](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)