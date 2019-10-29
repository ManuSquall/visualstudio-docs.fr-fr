---
title: Contrôle XmlMappedRange
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985359"
---
# <a name="xmlmappedrange-control"></a>Contrôle XmlMappedRange
  Le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est une plage qui est créée uniquement lorsqu’un élément de schéma non répétitif est mappé sur une cellule dans Microsoft Office Excel. Par exemple, lorsque l’attribut `maxOccurs` d’un élément de schéma est égal à 1. Une fois que Visual Studio a créé la plage mappée XML, vous pouvez la programmer directement sans avoir à parcourir le modèle objet Excel. Vous ne pouvez supprimer un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> dans Excel que si le mappage d’élément est supprimé.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Lier des données au contrôle
 Un contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> prend en charge la liaison à un champ de données unique (liaison de données simple). Le contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> peut prendre en charge la liaison de données complexe et est automatiquement créé lorsqu’un élément de schéma répétitif est mappé sur une cellule. Pour plus d’informations, consultez [ListObject Control](../vsto/listobject-control.md).

 Le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est lié à une source de données à l’aide de la propriété <xref:System.Windows.Forms.Control.DataBindings%2A>. Lorsqu’un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est ajouté à une cellule de feuille de calcul, Visual Studio génère automatiquement un jeu de données à partir des données dans les cellules mappées et lie le contrôle à ce jeu de données. La propriété de liaison de données par défaut de l' <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Si les données du jeu de données lié sont mises à jour par le biais d’un mécanisme quelconque, le contrôle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> reflète les modifications.

## <a name="formatting"></a>Mise en forme
 Vous pouvez appliquer la même mise en forme à un contrôle de <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> que vous pouvez appliquer à une <xref:Microsoft.Office.Interop.Excel.Range>. Cela inclut les bordures, les polices, le format de nombre et les styles.

## <a name="events"></a>événements
 Les événements disponibles pour le contrôle <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> sont les suivants :

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Voir aussi
- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)
- [Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
