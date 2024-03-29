---
title: Valider les données quand une nouvelle ligne est ajoutée au contrôle ListObject
description: Découvrez comment vous pouvez utiliser Visual Studio pour valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7002cdc0787850fc7be5a782f3cf3a2101d7593
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825717"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject
  Les utilisateurs peuvent ajouter de nouvelles lignes à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données. Vous pouvez valider les données de l’utilisateur avant d’approuver les modifications apportées à la source de données.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Validation des données
 Chaque fois qu’une ligne est ajoutée à un <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données, l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> est déclenché. Vous pouvez gérer cet événement pour effectuer la validation de vos données. Par exemple, si votre application requiert que seuls les employés âgés de 18 à 65 peuvent être ajoutés à la source de données, vérifiez que l’âge entré est compris dans cette plage avant que la ligne ne soit ajoutée.

> [!NOTE]
> Vous devez toujours vérifier l’entrée d’utilisateur sur le client, mais aussi sur le serveur. Pour plus d’informations, consultez [sécuriser les applications clientes](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Pour valider des données lorsqu’une nouvelle ligne est ajoutée à un ListObject lié aux données

1. Créez des variables pour l’ID et <xref:System.Data.DataTable> au niveau de la classe.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Créez un <xref:System.Data.DataTable> et ajoutez des exemples de colonnes et de données dans le `Startup` Gestionnaire d’événements de la `Sheet1` classe (dans un projet au niveau du document) ou de la `ThisAddIn` classe (dans un projet de complément VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Ajoutez du code au gestionnaire d’événements `list1_BeforeAddDataBoundRow` pour vérifier si l’âge entré est compris dans la plage autorisée.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.

## <a name="see-also"></a>Voir aussi
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject (contrôle)](../vsto/listobject-control.md)
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Comment : mapper des colonnes ListObject à des données](../vsto/how-to-map-listobject-columns-to-data.md)
