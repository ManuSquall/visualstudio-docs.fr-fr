---
title: "Comment : mettre en Cache par programmation une Source de données dans un Document Office | Documents Microsoft"
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
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e117243afff5cfa73cd7a27ad8ce0230d8fd512a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Comment : mettre en cache par programmation une source de données dans un document Office
  Vous pouvez ajouter par programmation un objet de données dans le cache de données dans un document en appelant le `StartCaching` élément de la méthode d’un ordinateur hôte, tel qu’un <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, ou <xref:Microsoft.Office.Tools.Excel.Worksheet>. Supprimer un objet de données à partir du cache de données en appelant le `StopCaching` méthode d’un élément hôte.  
  
 Le `StartCaching` (méthode) et le `StopCaching` sont privées, mais ils apparaissent dans IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Lorsque vous utilisez la `StartCaching` méthode pour ajouter un objet de données dans le cache de données, l’objet de données n’a pas besoin d’être déclaré avec le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut. Toutefois, l’objet de données doit respecter certaines exigences pour être ajouté au cache de données. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).  
  
### <a name="to-programmatically-cache-a-data-object"></a>Pour mettre en cache par programmation un objet de données  
  
1.  Déclarez l’objet de données au niveau de la classe, mais pas à l’intérieur d’une méthode. Cet exemple suppose que vous déclarez un <xref:System.Data.DataSet> nommé `dataSet1` que vous souhaitez mettre en cache par programmation.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Instanciez l’objet de données, puis appelez le `StartCaching` méthode de l’instance du document ou feuille de calcul et passez-lui le nom de l’objet de données.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>Pour arrêter la mise en cache un objet de données  
  
1.  Appelez le `StopCaching` méthode de l’instance du document ou feuille de calcul et passez-lui le nom de l’objet de données. Cet exemple suppose que vous avez un <xref:System.Data.DataSet> nommé `dataSet1` que vous souhaitez arrêter la mise en cache.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  N’appelez pas `StopCaching` du Gestionnaire d’événements pour le `Shutdown` événements d’un document ou une feuille de calcul. Au moment où le `Shutdown` événement est déclenché, il est trop tard pour modifier le cache de données. Pour plus d’informations sur la `Shutdown` événements, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cache de données](../vsto/caching-data.md)   
 [Comment : mettre en Cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Comment : mettre en Cache les données dans un Document protégé par mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [L’accès aux données dans des Documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Enregistrer des données](/visualstudio/data-tools/saving-data)  
  
  