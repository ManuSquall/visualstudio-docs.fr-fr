---
title: 'Procédure : Mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1be044131ab7248e971e5030f0d35467773587e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849920"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Procédure : Mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio
  Alors que la feuille de calcul est ouvert dans Visual Studio, vous pouvez mapper un schéma XML à une feuille de calcul. Vous utilisez les mêmes outils de Microsoft Office Excel que vous utilisez lorsque le classeur est ouvert en dehors de Visual Studio. Le projet Office crée les mêmes objets que vous mappiez le schéma à la feuille de calcul avant ou après avoir créé votre solution Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser les schémas XML en plusieurs parties dans les solutions Excel.  
  
## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Pour mapper un schéma XML à une feuille de calcul Excel dans Visual Studio  
  
1.  Ouvrez le projet de modèle ou de classeur Excel à l’intérieur de Visual Studio.  
  
2.  Cliquez dans la feuille de calcul pour déplacer le focus vers le concepteur.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur** .  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, voir [Procédure : Afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le **XML** de groupe, cliquez sur **Source**.  
  
     Le **Source XML** fenêtre s’ouvre.  
  
5.  Dans le **Source XML** fenêtre, cliquez sur **mappes XML**.  
  
     Le **mappes XML** boîte de dialogue s’ouvre.  
  
6.  Dans le **mappes XML** boîte de dialogue, cliquez sur **ajouter**.  
  
7.  Accédez à votre fichier de schéma, sélectionnez-le, puis cliquez sur **Open**.  
  
8.  Cliquez sur **OK**.  
  
     Le schéma est représenté dans le **Source XML** fenêtre. Dans votre projet, typé <xref:System.Data.DataSet> est généré en fonction du schéma et un <xref:System.Windows.Forms.BindingSource> est créé.  
  
9. Faire glisser des éléments à partir de la **Source XML** fenêtre aux endroits de votre feuille de calcul où vous souhaitez que les contrôles correspondants à créer.  
  
     Si vous faites glisser un élément de schéma non répétitif, le projet Office génère une <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle qui est automatiquement lié à la <xref:System.Windows.Forms.BindingSource>.  
  
     Si vous faites glisser un élément de schéma répétitif, le projet Office génère un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle qui n’est pas lié automatiquement à une source de données. Pour plus d’informations, consultez [schémas et données dans XML au niveau du document personnalisations](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Schémas XML et des données dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
