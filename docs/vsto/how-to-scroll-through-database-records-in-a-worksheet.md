---
title: 'Procédure : Parcourir les enregistrements de base de données dans une feuille de calcul'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f0b3c6a8a9292ceda03c9d0020b78d9518ca49d9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252029"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Procédure : Parcourir les enregistrements de base de données dans une feuille de calcul
  La procédure suivante indique comment utiliser le concepteur pour afficher un champ unique à partir d’une table de base de données dans une feuille de calcul Excel Microsoft Office, avec des contrôles qui permettent à l’utilisateur final de faire défiler tous les enregistrements.

 Vous pouvez utiliser le concepteur uniquement dans les projets au niveau du document. Toutefois, vous pouvez également ajouter des contrôles et les lier à des données par programmation au moment de l’exécution. Pour plus d’informations, consultez [Procédure pas à pas : Liaison de données simple dans un projet](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)de complément VSTO.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Pour faire défiler les enregistrements de base de données dans une feuille de calcul

1. Ouvrez un projet d’application Excel dans Visual Studio.

2. Ouvrez la fenêtre **sources de données** et créez une source de données à partir de la base de données. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. Développez la table qui contient les données que vous souhaitez afficher, puis sélectionnez la colonne spécifique.

4. Ouvrez la liste des contrôles et sélectionnez **NamedRange**.

5. Faites glisser <xref:Microsoft.Office.Tools.Excel.NamedRange> le contrôle sur la cellule où vous souhaitez que les données s’affichent.

6. À partir de l’onglet **Windows Forms** de la **boîte à outils**, ajoutez un <xref:System.Windows.Forms.BindingNavigator> contrôle à votre feuille de calcul et configurez les contrôles que vous souhaitez utiliser. Pour plus d’informations, consultez [vue d' &#40;ensemble&#41;du contrôle BindingNavigator Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Voir aussi
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
