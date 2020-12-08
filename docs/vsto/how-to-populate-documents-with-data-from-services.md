---
title: 'Comment : remplir des documents avec des données de services'
description: Découvrez comment vous pouvez utiliser les données des services de votre solution, et comment vous pouvez utiliser des contrôles de Windows Forms pour afficher les données dans un document.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4d8fb377896762672574c6ef5ff15b4e12b9e59
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845828"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Comment : remplir des documents avec des données de services

Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données dans votre solution, et vous pouvez même utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez tirer parti de contrôles appelés contrôles hôtes, qui sont des objets natifs dans Microsoft Office Excel et Microsoft Office Word qui ont été améliorés avec des événements et une fonctionnalité de liaison de données. Pour plus d’informations, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

L’exemple suivant montre comment ajouter des contrôles liés aux données à des documents au moment du design. Pour obtenir un exemple d’ajout de contrôles liés aux données dans les compléments VSTO au moment de l’exécution, consultez [procédure pas à pas : liaison à des données à partir d’un service dans un projet de complément VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Pour remplir un projet au niveau du document avec les données d’un service Web

1. Ouvrez la fenêtre **Sources de données** et créez une source de données de service pour votre projet. Pour plus d’informations, consultez [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

2. Faites glisser le tableau ou le champ que vous souhaitez à partir de la fenêtre **Sources de données** vers votre document.

     Un contrôle est créé sur le document, un <xref:System.Windows.Forms.BindingSource> lié à la classe d’objet dans votre projet est créé, et des classes sont générées pour le service.

3. Dans votre code, créez une instance de la classe de service Web à laquelle vous vous êtes connecté à l’étape 1.

4. Si des propriétés sont requises pour la communication avec le service Web, créez des instances de ces propriétés.

5. Créez et envoyez une demande de données à l’aide des méthodes exposées par le service web et des éventuelles instances de propriétés que vous avez créées à l’étape 4.

     Les méthodes que vous utilisez dépendent de ce que propose le service Web.

6. Assignez la réponse aux données du service Web à la <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété du <xref:System.Windows.Forms.BindingSource> .

Lorsque vous exécutez le projet, les contrôles affichent le premier enregistrement de la source de données. Vous pouvez activer l’exploration des enregistrements en gérant les événements monétaires à l’aide des objets dans le <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Voir aussi

- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Comment : remplir des feuilles de calcul avec des données d’une base de données](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Comment : remplir des documents avec des données d’objets](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)