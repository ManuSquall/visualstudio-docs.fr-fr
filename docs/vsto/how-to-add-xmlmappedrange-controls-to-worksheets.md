---
title: 'Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul'
description: Apprenez que quand vous mappez un élément XML à une cellule dans Microsoft Office Excel, Visual Studio ajoute automatiquement un contrôle XmlMappedRange à votre feuille de calcul.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 7e807a5673f27da6a852fd2c83347d1348f1f6fd
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844411"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul
  Quand vous mappez un élément XML à une cellule dans Microsoft Office Excel, Visual Studio ajoute automatiquement un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle à votre feuille de calcul.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle n’est pas disponible dans la **boîte à outils** ou la fenêtre **sources de données** . En outre, vous ne pouvez pas créer de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôles par programme.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Pour ajouter un contrôle XMLMappedRange à une feuille de calcul

1. Ouvrez le classeur Excel dans le concepteur Visual Studio.

2. Ouvrez la feuille de calcul dans laquelle vous souhaitez ajouter le contrôle.

3. Dans l’onglet **développeur** , cliquez sur **source**.

    > [!NOTE]
    > Si l’onglet **développeur** n’est pas visible sur le ruban, vous devez l’activer. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Le volet Office **source XML** s’affiche.

4. Dans le volet Office **source XML** , cliquez sur **Mappages XML**.

5. Dans la boîte de dialogue **Mappages XML** , cliquez sur **Ajouter**.

     La boîte de dialogue **source XML** s’affiche.

6. Sélectionnez un schéma XML dans la boîte de dialogue **source XML** , puis cliquez sur **ouvrir**.

     Le schéma est ajouté à la boîte de dialogue **Mappages XML** .

7. Dans la boîte de dialogue **Mappages XML** , cliquez sur **OK**.

8. Faites glisser un élément du volet Office **source XML** vers une cellule de la feuille de calcul.

     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est créé et ajouté au projet.

    > [!NOTE]
    > Si vous faites glisser un élément parent à partir du volet Office **source XML** , un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle est créé.

## <a name="see-also"></a>Voir aussi
- [Contrôle XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
