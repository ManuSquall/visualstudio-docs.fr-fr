---
title: 'Procédure : Remplir des feuilles de calcul avec des données à partir d’une base de données'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1169ea54ffbc0d0437204ed4491e2b8cc68a4a04
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865617"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Procédure : Remplir des feuilles de calcul avec des données à partir d’une base de données

Vous pouvez accéder des données dans les projets Office au niveau du document de la même façon que vous accéder aux données dans les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel qui ont été améliorés avec des événements et une fonctionnalité de liaison de données. Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

L'exemple suivant montre comment ajouter des contrôles liés aux données dans les projets au niveau du document à l'aide d'un concepteur. Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans les projets au niveau de l’application en cours d’exécution, consultez [procédure pas à pas : Liaison de données complexe dans un projet de complément VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [How do I: Transférer des données dans une feuille de calcul Excel ? ](http://go.microsoft.com/fwlink/?LinkID=130277), et [How do I: Pour consommer des données de base de données dans Excel ? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Ajouter un contrôle lié aux données à une feuille de calcul au moment du design

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Pour remplir une feuille de calcul avec des données à partir d’une base de données

1.  Ouvrez un projet de document Excel dans Visual Studio, avec la feuille de calcul ouverte dans le concepteur.

2.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3.  Faites glisser le champ ou la table que vous souhaitez à partir de la **des Sources de données** fenêtre à votre feuille de calcul.

Un des contrôles suivants est créé sur la feuille de calcul :

-   Si vous faites glisser un champ, un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle est créé sur la feuille de calcul. Pour plus d’informations, consultez [contrôle NamedRange](../vsto/namedrange-control.md).

-   Si vous faites glisser une table, un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle est créé sur la feuille de calcul. Pour plus d’informations, consultez [contrôle ListObject](../vsto/listobject-control.md).

Vous pouvez ajouter un autre contrôle en sélectionnant la table ou le champ dans le **des Sources de données** fenêtre, puis en choisissant un autre contrôle dans la liste déroulante.

## <a name="objects-in-the-project"></a>Objets dans le projet

Outre le contrôle, les objets de données suivants sont automatiquement ajoutés à votre projet :

-   Un dataset typé qui encapsule les tables de données auxquelles vous êtes connecté dans la base de données. Pour plus d’informations, consultez [outils de Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au dataset typé. Pour plus d’informations, consultez [vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Un TableAdapter qui connecte le dataset typé à la base de données. Pour plus d’informations, consultez [vue d’ensemble de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

-   Un TableAdapterManager, qui est utilisé pour coordonner des adaptateurs de table dans le jeu de données pour activer les mises à jour hiérarchiques. Pour plus d’informations, consultez [mise à jour hiérarchique](../data-tools/hierarchical-update.md) et [TableAdapterManager référence](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Lorsque vous exécutez le projet, le contrôle affiche le premier enregistrement de la source de données. Vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> pour permettre aux utilisateurs de faire défiler les enregistrements.

### <a name="to-scroll-through-the-records"></a>Pour faire défiler les enregistrements

-   Utilisez les méthodes <xref:System.Windows.Forms.BindingSource> telles que <xref:System.Windows.Forms.BindingSource.MoveNext%2A> et <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Pour plus d’informations sur l’envoi des mises à jour pour le dataset typé et la base de données, consultez [Comment : Mettre à jour une source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Voir aussi

- [Lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Guide pratique pour Remplir des documents avec des données à partir d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Guide pratique pour Remplir des documents avec des données à partir d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Guide pratique pour Remplir des documents avec des données à partir des services](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Guide pratique pour Mettre à jour une source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Comment faire Transférer des données dans une feuille de calcul Excel](http://go.microsoft.com/fwlink/?LinkID=130277)
- [Comment faire Pour consommer des données de base de données dans Excel ?](http://go.microsoft.com/fwlink/?LinkID=130287)