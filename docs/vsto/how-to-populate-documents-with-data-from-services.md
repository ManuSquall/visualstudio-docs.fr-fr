---
title: 'Comment : remplir des documents avec des données à partir des services'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ac901b524818086d6dbf23b7b55487054170b3e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758540"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Comment : remplir des documents avec des données à partir des services

Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel et Microsoft Office Word qui ont été améliorés avec des événements et une fonctionnalité de liaison de données. Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

L’exemple suivant montre comment ajouter des contrôles liés aux données à des documents au moment du design. Pour obtenir un exemple montrant comment ajouter des contrôles liés aux données dans des Compléments VSTO au moment de l’exécution, consultez [procédure pas à pas : lier à des données à partir d’un service dans un projet de complément VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [comment faire pour interagir avec les services web à partir de Microsoft Excel ?](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Pour remplir un projet au niveau du document avec des données à partir d’un service web

1.  Ouvrez la fenêtre **Sources de données** et créez une source de données de service pour votre projet. Pour plus d’informations, consultez [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

2.  Faites glisser le tableau ou le champ que vous souhaitez à partir de la fenêtre **Sources de données** vers votre document.

     Un contrôle est créé sur le document, un <xref:System.Windows.Forms.BindingSource> lié à la classe d’objet dans votre projet est créé, et des classes sont générées pour le service.

3.  Dans votre code, créez une instance de la classe de service web auquel vous connecté à l’étape 1.

4.  S’il existe des propriétés qui sont requises pour la communication avec le service web, créer des instances de ces propriétés.

5.  Créez et envoyez une demande de données à l’aide des méthodes exposées par le service web et des éventuelles instances de propriétés que vous avez créées à l’étape 4.

     Les méthodes que vous utilisez dépendent de l’offre de ce que le service web.

6.  Affectez la réponse du service web pour le <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété de la <xref:System.Windows.Forms.BindingSource>.

Lorsque vous exécutez le projet, les contrôles affichent le premier enregistrement de la source de données. Vous pouvez activer l’exploration des enregistrements en gérant les événements monétaires à l’aide des objets dans le <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Voir aussi

- [Lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Comment : remplir des feuilles de calcul avec des données à partir d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Comment : remplir des documents avec des données à partir d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Comment : remplir des documents avec des données à partir d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Comment : mettre à jour une source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)