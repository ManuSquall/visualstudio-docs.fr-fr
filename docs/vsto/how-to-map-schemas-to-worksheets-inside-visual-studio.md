---
title: 'Comment : mapper des schémas à des feuilles de calcul dans Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538136"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Comment : mapper des schémas à des feuilles de calcul dans Visual Studio
  Vous pouvez mapper un schéma XML à une feuille de calcul alors que la feuille de calcul est ouverte dans Visual Studio. Vous utilisez le même Microsoft Office les outils Excel que vous utilisez lorsque le classeur est ouvert en dehors de Visual Studio. Le projet Office crée les mêmes objets si vous mappez le schéma à la feuille de calcul avant ou après la création de votre solution Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Vous ne pouvez pas utiliser des schémas XML en plusieurs parties dans les solutions Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Pour mapper un schéma XML à une feuille de calcul Excel dans Visual Studio

1. Ouvrez le classeur Excel ou le projet de modèle dans Visual Studio.

2. Cliquez dans la feuille de calcul pour déplacer le focus sur le concepteur.

3. Dans le ruban, cliquez sur l'onglet **Développeur** .

    > [!NOTE]
    > Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d’informations, consultez [Comment : afficher l’onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Dans le groupe **XML** , cliquez sur **source**.

     La fenêtre **source XML** s’ouvre.

5. Dans la fenêtre **source XML** , cliquez sur **Mappages XML**.

     La boîte de dialogue **Mappages XML** s’ouvre.

6. Dans la boîte de dialogue **Mappages XML** , cliquez sur **Ajouter**.

7. Accédez à votre fichier de schéma, sélectionnez-le, puis cliquez sur **ouvrir**.

8. Cliquez sur **OK**.

     Le schéma est représenté dans la fenêtre **source XML** . Dans votre projet, un type <xref:System.Data.DataSet> est généré en fonction du schéma et un <xref:System.Windows.Forms.BindingSource> est créé.

9. Faites glisser les éléments de la fenêtre **source XML** vers les emplacements de la feuille de calcul où vous souhaitez créer les contrôles correspondants.

     Si vous faites glisser un élément de schéma non répétitif, le projet Office génère un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle qui est automatiquement lié à <xref:System.Windows.Forms.BindingSource> .

     Si vous faites glisser un élément de schéma répétitif, le projet Office génère un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle qui n’est pas automatiquement lié à une source de données. Pour plus d’informations, consultez [schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Voir aussi
- [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
