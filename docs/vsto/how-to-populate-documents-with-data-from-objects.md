---
title: "Comment : remplir des Documents avec les données d’objets | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2ecc8e8ce76c2212d9921cc9b15ead7a7b22316e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Comment : remplir des documents avec les données d'objets
  Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données d’un objet dans votre solution. Par ailleurs, vous pouvez utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez afficher les données à l'aide de contrôles hôtes. Les contrôles hôtes sont des objets natifs dans Microsoft Office Word qui ont été améliorés avec les événements et la fonctionnalité de liaison de données. Pour plus d'informations, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Vous devez effectuer trois étapes de base pour remplir le document à l’aide des données d’un objet :  
  
-   Ajoutez un contrôle au document que vous pouvez lier aux données.  
  
-   Ajoutez un objet de données au document.  
  
-   Connectez l’objet de données à BindingSource.   
  
## <a name="adding-a-data-object"></a>Ajout d’un objet de données  
  
#### <a name="to-add-a-data-object"></a>Pour ajouter un objet de données  
  
-   Ouvrez la fenêtre **Sources de données** , puis créez une source de données à partir d’un objet. Pour plus d’informations, consultez [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>Connexion de l’objet de données à BindingSource  
 Dans les projets au niveau du document, vous ajoutez les contrôles à votre document et les liez aux données au moment du design.  
  
 Dans les projets de complément VSTO, vous créez les contrôles et les liez au moment de l’exécution.  
  
### <a name="document-level-projects"></a>Projets au niveau du document  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Pour connecter l’objet de données à BindingSource  
  
1.  Faites glisser le champ de données que vous souhaitez de la fenêtre **Sources de données** vers votre document. Cela entraîne la création automatique d’un contrôle.  
  
2.  Dans votre code, créez une instance du type de l’objet que vous avez choisi pour la source de données.  
  
3.  Assignez l’instance à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="application-level-projects"></a>Projets de niveau application  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Pour connecter l’objet de données à BindingSource  
  
1.  Dans votre code, créez une instance du type de l’objet associé à la source de données.  
  
2.  Créez une instance de <xref:System.Windows.Forms.BindingSource>.  
  
3.  Assignez l’instance de la source de données à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.  
  
4.  Ajoutez la source de données en tant que liaison de données au contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 
 [Ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources)   
 [Lier des contrôles Windows Forms à des données dans Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Comment : remplir des Documents avec les données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : mettre à jour une Source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Connexion aux données dans les Applications Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Vue d'ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  