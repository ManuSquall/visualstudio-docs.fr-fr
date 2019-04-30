---
title: 'Procédure : Ajouter des contrôles XMLMappedRange aux feuilles de calcul'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60f1fe8330e3a40676738c4187273ee60215db6d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427431"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Procédure : Ajouter des contrôles XMLMappedRange aux feuilles de calcul
  Lorsque vous mappez un élément XML à une cellule dans Microsoft Office Excel, Visual Studio ajoute automatiquement un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle à votre feuille de calcul.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle n’est pas disponible sur le **boîte à outils** ou **des Sources de données** fenêtre. En outre, vous ne pouvez pas créer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> par programmation des contrôles.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Pour ajouter un contrôle XMLMappedRange à une feuille de calcul

1. Ouvrez le classeur Excel dans le concepteur Visual Studio.

2. Ouvrez la feuille de calcul où vous souhaitez ajouter le contrôle.

3. Sur le **développeur** , cliquez sur **Source**.

    > [!NOTE]
    > Si le **développeur** onglet n’est pas visible sur le ruban, vous devez l’activer. Pour plus d'informations, voir [Procédure : Afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Le **Source XML** volet s’affiche.

4. Dans le **Source XML** volet de tâches, cliquez sur **mappes XML**.

5. Dans le **mappes XML** boîte de dialogue, cliquez sur **ajouter**.

     Le **Source XML** boîte de dialogue s’affiche.

6. Sélectionnez un schéma XML à partir de la **Source XML** boîte de dialogue et cliquez sur **Open**.

     Le schéma est ajouté à la **mappes XML** boîte de dialogue.

7. Dans le **mappes XML** boîte de dialogue, cliquez sur **OK**.

8. Faites glisser un élément à partir de la **Source XML** volet des tâches vers une cellule sur la feuille de calcul.

     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est créé et ajouté au projet.

    > [!NOTE]
    > Si vous faites glisser un élément parent à partir de la **Source XML** volet des tâches, un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle est créé.

## <a name="see-also"></a>Voir aussi
- [XmlMappedRange control](../vsto/xmlmappedrange-control.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Guide pratique pour Mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
