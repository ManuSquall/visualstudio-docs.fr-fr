---
title: 'Procédure : Mettre en cache par programmation une source de données dans un document Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3db60729facffdfd42553f95215e154de528436f
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804443"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Procédure : Mettre en cache par programmation une source de données dans un document Office
  Vous pouvez ajouter un objet de données par programmation au cache de données dans un document en appelant le `StartCaching` élément de la méthode d’un ordinateur hôte, tel qu’un <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, ou <xref:Microsoft.Office.Tools.Excel.Worksheet>. Suppression d’un objet de données à partir du cache de données en appelant le `StopCaching` méthode d’un élément hôte.

 Le `StartCaching` (méthode) et le `StopCaching` sont privées, mais ils apparaissent dans IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Lorsque vous utilisez le `StartCaching` méthode pour ajouter un objet de données au cache de données, l’objet de données ne doit pas être déclaré avec le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut. Toutefois, l’objet de données doit remplir certaines conditions à ajouter au cache de données. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Pour mettre en cache par programme un objet de données

1.  Déclarez l’objet de données au niveau de la classe, mais pas à l’intérieur d’une méthode. Cet exemple suppose que vous déclarez un <xref:System.Data.DataSet> nommé `dataSet1` que vous souhaitez mettre en cache par programmation.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2.  Instanciez l’objet de données, puis appelez le `StartCaching` méthode de l’instance de document ou feuille de calcul et transmettez le nom de l’objet de données.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Pour arrêter la mise en cache un objet de données

1.  Appelez le `StopCaching` méthode de l’instance de document ou feuille de calcul et transmettez le nom de l’objet de données. Cet exemple suppose que vous avez un <xref:System.Data.DataSet> nommé `dataSet1` que vous souhaitez arrêter la mise en cache.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    >  N’appelez pas `StopCaching` du Gestionnaire d’événements pour le `Shutdown` événement d’un document ou une feuille de calcul. Au moment où le `Shutdown` événement est déclenché, il est trop tard pour modifier le cache de données. Pour plus d’informations sur la `Shutdown` événement, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Voir aussi

- [Données du cache](../vsto/caching-data.md)
- [Guide pratique pour Mettre en cache les données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Guide pratique pour Cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)
- [Enregistrer des données](../data-tools/saving-data.md)
