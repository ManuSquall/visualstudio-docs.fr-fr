---
title: Mettre en cache une source de données dans un document Office par programmation
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ec3a38d109de561e3cba77951764dd8dd9479df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544766"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Comment : mettre en cache par programmation une source de données dans un document Office
  Vous pouvez ajouter par programmation un objet de données au cache de données dans un document en appelant la `StartCaching` méthode d’un élément hôte, tel que <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> ou <xref:Microsoft.Office.Tools.Excel.Worksheet> . Supprimez un objet de données du cache de données en appelant la `StopCaching` méthode d’un élément hôte.

 La `StartCaching` méthode et la `StopCaching` méthode sont privées, mais elles apparaissent dans IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Lorsque vous utilisez la `StartCaching` méthode pour ajouter un objet de données au cache de données, l’objet de données n’a pas besoin d’être déclaré avec l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut. Toutefois, l’objet de données doit répondre à certaines exigences pour être ajouté au cache de données. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Pour mettre en cache un objet de données par programmation

1. Déclarez l’objet de données au niveau de la classe, et non à l’intérieur d’une méthode. Cet exemple suppose que vous déclarez un <xref:System.Data.DataSet> nommé `dataSet1` que vous souhaitez mettre en cache par programmation.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Instanciez l’objet de données, puis appelez la `StartCaching` méthode de l’instance de document ou de feuille de calcul et transmettez le nom de l’objet de données.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Pour arrêter la mise en cache d’un objet de données

1. Appelez la `StopCaching` méthode de l’instance du document ou de la feuille de calcul et transmettez le nom de l’objet de données. Cet exemple suppose que vous avez un <xref:System.Data.DataSet> nommé `dataSet1` dont vous souhaitez arrêter la mise en cache.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > N’appelez pas `StopCaching` à partir du gestionnaire d’événements pour l' `Shutdown` événement d’un document ou d’une feuille de calcul. Lorsque l' `Shutdown` événement est déclenché, il est trop tard pour modifier le cache de données. Pour plus d’informations sur l' `Shutdown` événement, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Voir aussi

- [Données de cache](../vsto/caching-data.md)
- [Procédure : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accéder aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)
- [Enregistrer les données](../data-tools/save-data-back-to-the-database.md)
