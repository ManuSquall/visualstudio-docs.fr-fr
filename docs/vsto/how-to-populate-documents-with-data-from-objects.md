---
title: 'Comment : remplir des documents avec des données à partir d’objets'
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
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef3d1441f9587bceeca0c4aacdc054a4769a2369
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758110"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Comment : remplir des documents avec des données à partir d’objets

Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données d’un objet dans votre solution. Par ailleurs, vous pouvez utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez afficher les données à l'aide de contrôles hôtes. Les contrôles hôtes sont des objets natifs dans Microsoft Office Word qui ont été améliorés avec les événements et la fonctionnalité de liaison de données. Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Vous devez effectuer trois étapes de base pour remplir le document à l’aide des données d’un objet :

-   Ajoutez un contrôle au document que vous pouvez lier aux données.

-   Ajoutez un objet de données au document.

-   Connectez l’objet de données à BindingSource.

## <a name="to-add-a-data-object"></a>Pour ajouter un objet de données

Pour ajouter un objet de données, ouvrez le **des Sources de données** fenêtre et créer une source de données à partir d’un objet. Pour plus d’informations, consultez [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Connecter l’objet de données à BindingSource

Dans les projets au niveau du document, vous ajoutez les contrôles à votre document et les liez aux données au moment du design.

Dans les projets de complément VSTO, vous créez les contrôles et les liez au moment de l’exécution.

### <a name="document-level-projects"></a>Projets au niveau du document

Pour vous connecter à l’objet de données à BindingSource :

1.  Faites glisser le champ de données que vous souhaitez de la fenêtre **Sources de données** vers votre document. Cela entraîne la création automatique d’un contrôle.

2.  Dans votre code, créez une instance du type de l’objet que vous avez choisi pour la source de données.

3.  Assignez l’instance à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.

### <a name="application-level-projects"></a>Projets de niveau application

Pour vous connecter à l’objet de données à BindingSource :

1.  Dans votre code, créez une instance du type de l’objet associé à la source de données.

2.  Créez une instance de <xref:System.Windows.Forms.BindingSource>.

3.  Assignez l’instance de la source de données à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.

4.  Ajoutez la source de données en tant que liaison de données au contrôle.

## <a name="see-also"></a>Voir aussi

- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)
- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Comment : remplir des documents avec des données à partir d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Comment : mettre à jour une source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)