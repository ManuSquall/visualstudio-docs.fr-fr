---
title: Utiliser des contrôles Windows Forms sur des feuilles de calcul Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032ee551ff04590ccdb8744c1274b137dec0b756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982316"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Utiliser des contrôles Windows Forms sur des feuilles de calcul Excel
  Vous pouvez ajouter des contrôles Windows Forms à vos classeurs Excel Microsoft Office de la même manière que vous ajoutez des contrôles à Windows Forms. Pour obtenir des informations générales sur l’utilisation des contrôles sur les documents, consultez [vue d’ensemble des contrôles de Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Considérations relatives aux contrôles pour Excel
 Certaines considérations spécifiques à Excel sont à prendre en compte.

### <a name="match-control-size-to-cell-size"></a>Faire correspondre la taille du contrôle à la taille des cellules
 Vous pouvez configurer le contrôle pour qu’il soit redimensionné automatiquement quand la taille de la cellule parente change. Pour plus d’informations, consultez [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Ajouter des composants qui sont partagés par toutes les feuilles de calcul
 Vous pouvez ajouter des composants que vous souhaitez partager parmi toutes les feuilles de calcul, comme un <xref:System.Data.DataSet>, au Concepteur de classeurs plutôt qu’aux feuilles de calcul. Le composant apparaîtra dans la barre d’état des composants.

### <a name="formula-for-embedding-controls"></a>Formule pour l’incorporation de contrôles
 Quand vous sélectionnez un contrôle dans Excel, vous voyez **=EMBED("WinForms.Control.Host","")** dans la **Barre de formule**. Ce texte est nécessaire et ne doit pas être supprimé.

## <a name="see-also"></a>Voir aussi
- [Comment : redimensionner des contrôles dans des cellules de feuille de calcul](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Comment : masquer des contrôles sur des feuilles de calcul lors de l’impression](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Procédure pas à pas : modifier la mise en forme d’une feuille de calcul à l’aide](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Procédure pas à pas : affichage de texte dans une zone de texte d’une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Procédure pas à pas : mettre à jour un graphique dans une feuille de calcul à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
