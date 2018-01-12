---
title: "XmlMappedRange, contrôle | Documents Microsoft"
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
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f4b78da11efafff45f34b3dc4ab9e7f1349a2e8a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange, contrôle
  Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle est une plage qui est créée uniquement lorsqu’un élément de schéma non répétitif est mappé sur une cellule dans Microsoft Office Excel. Par exemple, lorsque le `maxOccurs` attribut d’un élément de schéma est égal à 1. Après que Visual Studio a créé la plage mappée en XML, vous pouvez le programmer directement sans avoir à parcourir le modèle objet Excel. Vous ne pouvez supprimer un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle dans Excel lorsque le mappage d’élément est supprimé.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire utiliser le mappage XML dans Excel ?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="binding-data-to-the-control"></a>Liaison de données au contrôle  
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle prend en charge la liaison à un champ de données (liaison de données simple). Le <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle peut prend en charge la liaison de données complexe et est automatiquement créé lorsqu’un élément de schéma répétitif est mappé à une cellule. Pour plus d'informations, consultez [ListObject Control](../vsto/listobject-control.md).  
  
 Le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle sont liés à une source de données à l’aide de la <xref:System.Windows.Forms.Control.DataBindings%2A> propriété. Lorsqu’un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est ajouté à une cellule de feuille de calcul, Visual Studio génère automatiquement un jeu de données à partir des données des cellules mappées et lie le contrôle à ce jeu de données. La propriété de liaison de données par défaut de la <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> est <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Si les données dans le jeu de données liée sont mis à jour via un mécanisme quelconque, la <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle reflète les modifications.  
  
## <a name="formatting"></a>Mise en forme  
 Vous pouvez appliquer la même mise en forme à un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle que vous pouvez appliquer à un <xref:Microsoft.Office.Interop.Excel.Range>. Cela inclut les bordures, les polices, le format de nombre et les styles.  
  
## <a name="events"></a>Événements  
 Les événements disponibles pour le <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle sont :  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>Voir aussi  
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : ajouter des contrôles XMLMappedRange aux feuilles de calcul](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  