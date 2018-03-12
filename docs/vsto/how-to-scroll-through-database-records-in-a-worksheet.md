---
title: "Comment : faire défiler des enregistrements de base de données dans une feuille de calcul | Documents Microsoft"
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7e6ea8269401a8b026da2562eff96e50820e0a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Comment : parcourir les enregistrements de base de données dans une feuille de calcul
  La procédure suivante montre comment utiliser le concepteur pour afficher un champ d’une table de base de données dans une feuille de calcul Microsoft Office Excel, avec des contrôles qui permettent aux utilisateurs finaux de faire défiler tous les enregistrements.  
  
 Vous pouvez utiliser le concepteur uniquement dans les projets au niveau du document. Toutefois, vous pouvez également ajouter des contrôles et les lier aux données par programme en cours d’exécution. Pour plus d’informations, consultez [procédure pas à pas : liaison de données Simple dans VSTO complément Project](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Faire défiler des enregistrements de base de données dans une feuille de calcul  
  
1.  Ouvrez un projet d’application Excel dans Visual Studio.  
  
2.  Ouvrez le **des Sources de données** fenêtre et créer une source de données à partir de la base de données. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).  
  
3.  Développez la table qui contient les données que vous souhaitez afficher et sélectionnez la colonne spécifique.  
  
4.  Ouvrez la liste de contrôles et sélectionnez **NamedRange**.  
  
5.  Faites glisser le <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle vers la cellule où vous souhaitez afficher les données.  
  
6.  À partir de la **Windows Forms** onglet de la **boîte à outils**, ajoutez un <xref:System.Windows.Forms.BindingNavigator> le contrôle à votre feuille de calcul et configurez les contrôles que vous souhaitez utiliser. Pour plus d’informations, consultez [vue d’ensemble du contrôle BindingNavigator &#40; Windows Forms &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  