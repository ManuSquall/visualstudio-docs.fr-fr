---
title: 'Procédure : Remplir des documents avec des données à partir d’une base de données'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1522b2567c05a9c3a61091813a8b5e18315433f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863446"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Procédure : Remplir des documents avec des données à partir d’une base de données

Vous pouvez accéder aux projets au niveau du document pour Microsoft Office de la même façon que vous accédez aux données des projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données à partir d'une base de données dans votre solution, et vous pouvez utiliser des contrôles Windows Forms pour afficher les données.

En outre, vous pouvez afficher les données à l'aide de contrôles hôtes. Les contrôles hôtes sont des objets natifs dans Microsoft Office Word qui ont été améliorés avec les événements et la fonctionnalité de liaison de données. Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

L'exemple suivant montre comment ajouter des contrôles liés aux données dans les projets au niveau du document à l'aide d'un concepteur. Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans les projets de complément VSTO au moment de l’exécution, consultez [procédure pas à pas : Liaison de données simple dans un projet de complément VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [lier des données au contenu de Word 2007 contrôle à l’aide de Visual Studio Tools pour Office system (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).

## <a name="add-a-control-to-a-document-at-design-time"></a>Ajouter un contrôle à un document au moment du design

### <a name="to-populate-a-document-with-data-from-a-database"></a>Remplir un document avec les données d'une base de données

1.  Ouvrez un projet au niveau du document Word dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], avec le document ouvert dans le concepteur.

2.  Ouvrez le **des Sources de données** fenêtre et créer une source de données à partir d’une base de données. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3.  Faites glisser le champ souhaité à partir de la **des Sources de données** fenêtre vers votre document.

Un contrôle de contenu est ajouté au document. Le type de contrôle de contenu dépend du type de données du champ sélectionné. Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md).

Vous pouvez ajouter un autre contrôle en sélectionnant le champ de données dans le **des Sources de données** fenêtre, puis en choisissant un autre contrôle dans la liste déroulante.

## <a name="objects-in-the-project"></a>Objets dans le projet

Outre le contrôle, les objets de données suivants sont automatiquement ajoutés à votre projet :

-   Un dataset typé qui encapsule les tables de données auxquelles vous êtes connecté dans la base de données. Pour plus d’informations, consultez [outils de Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au dataset typé. Pour plus d’informations, consultez [vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Un TableAdapter qui connecte le dataset typé à la base de données. Pour plus d’informations, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).

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
- [Guide pratique pour Mettre à jour une source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Utiliser des fichiers de base de données locale dans la vue d’ensemble des solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)