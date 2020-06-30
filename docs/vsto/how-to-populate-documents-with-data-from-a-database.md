---
title: 'Comment : remplir des documents avec des données d’une base de données'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8470ec4acf686c016088c5f474539a1ab7ed85df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547197"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Comment : remplir des documents avec des données d’une base de données

Vous pouvez accéder aux projets au niveau du document pour Microsoft Office de la même façon que vous accédez aux données des projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données à partir d'une base de données dans votre solution, et vous pouvez utiliser des contrôles Windows Forms pour afficher les données.

En outre, vous pouvez afficher les données à l'aide de contrôles hôtes. Les contrôles hôtes sont des objets natifs dans Microsoft Office Word qui ont été améliorés avec les événements et la fonctionnalité de liaison de données. Pour plus d’informations, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

L'exemple suivant montre comment ajouter des contrôles liés aux données dans les projets au niveau du document à l'aide d'un concepteur. Pour obtenir un exemple d’ajout de contrôles liés aux données dans des projets de complément VSTO au moment de l’exécution, consultez [procédure pas à pas : liaison de données simple dans un projet de complément VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez [liaison de données aux contrôles de contenu Word 2007 à l’aide de Visual Studio Tools pour Office System (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Ajouter un contrôle à un document au moment du design

### <a name="to-populate-a-document-with-data-from-a-database"></a>Remplir un document avec les données d'une base de données

1. Ouvrez un projet au niveau du document Word dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], avec le document ouvert dans le concepteur.

2. Ouvrez la fenêtre **sources de données** et créez une source de données à partir d’une base de données. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. Faites glisser le champ de votre choix de la fenêtre **sources de données** vers votre document.

Un contrôle de contenu est ajouté au document. Le type de contrôle de contenu dépend du type de données du champ sélectionné. Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md).

Vous pouvez ajouter un contrôle différent en sélectionnant le champ de données dans la fenêtre **sources de données** , puis en choisissant un autre contrôle dans la liste déroulante.

## <a name="objects-in-the-project"></a>Objets du projet

Outre le contrôle, les objets de données suivants sont automatiquement ajoutés à votre projet :

- Un dataset typé qui encapsule les tables de données auxquelles vous êtes connecté dans la base de données. Pour plus d’informations, consultez [outils de jeu de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un <xref:System.Windows.Forms.BindingSource> qui connecte le contrôle au dataset typé. Pour plus d’informations, consultez [vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter qui connecte le DataSet typé à la base de données. Pour plus d’informations, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).

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
- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Vue d’ensemble de l’utilisation des fichiers de base de données locaux dans les solutions Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)