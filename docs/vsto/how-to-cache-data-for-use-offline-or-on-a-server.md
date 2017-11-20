---
title: "Comment : mettre en Cache des données pour une utilisation hors connexion ou sur un serveur | Documents Microsoft"
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
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a8da60aa9d9dc3ab7becb56b3b4c7701494daef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur
  Vous pouvez marquer un élément de données doit être mis en cache dans le document, afin qu’il soit disponible hors connexion. Cela rend également possible pour les données dans le document à être manipulées par un autre code lorsque le document est stocké sur un serveur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez marquer un élément de données doit être mis en cache lorsque l’élément de données est déclaré dans votre code, ou, si vous utilisez un <xref:System.Data.DataSet>, en définissant une propriété le **propriétés** fenêtre. Si vous mettez en cache un élément de données qui n’est pas un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>, assurez-vous qu’il remplit les critères de mise en cache dans le document. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Jeux de données créés à l’aide de Visual Basic qui sont marqués comme **mises en cache** et **WithEvents** (y compris les jeux de données qui est déplacées de la **des Sources de données** fenêtre ou **Boîte à outils** qui ont le **CacheInDocument** propriété **True**) ont un trait de soulignement devant leur nom dans le cache. Par exemple, si vous créez un dataset et nommez **clients**, le <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nom sera **_Clients** dans le cache. Lorsque vous utilisez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour accéder à cet élément de mise en cache, vous devez spécifier **_Clients** au lieu de **clients**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Données en cache dans le document à l’aide de code  
  
1.  Déclarez un champ public ou une propriété pour l’élément de données en tant que membre d’une classe d’élément hôte dans votre projet, telles que la `ThisDocumen`classe t dans un projet Word ou la `ThisWorkbook` classe dans un projet Excel.  
  
2.  Appliquer le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au membre pour marquer l’élément de données à stocker dans le cache de données du document. L’exemple suivant applique cet attribut à une déclaration de champ pour un <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Ajoutez du code pour créer une instance de l’élément de données et, le cas échéant, à le charger à partir de la base de données.  
  
     L’élément de données est chargé uniquement lorsqu’il est créé en premier ; par la suite, le cache reste associée au document et vous devez écrire le code pour mettre à jour.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Pour mettre en cache un dataset dans le document à l’aide de la fenêtre Propriétés  
  
1.  Ajouter le jeu de données au projet à l’aide des outils dans le concepteur Visual Studio, par exemple, en ajoutant une source de données dans votre projet en utilisant le **des Sources de données** fenêtre.  
  
2.  Créez une instance du jeu de données si vous ne pas déjà un et sélectionnez l’instance dans le concepteur.  
  
3.  Dans le **propriétés** , configurez la **CacheInDocument** propriété **True**.  
  
     Pour plus d’informations, consultez [propriétés dans les projets Office](../vsto/properties-in-office-projects.md).  
  
4.  Dans le **propriétés** , configurez la **modificateurs** propriété **Public** (par défaut, il est **interne**).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cache de données](../vsto/caching-data.md)   
 [Comment : mettre en Cache par programmation une Source de données dans un Document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Comment : mettre en Cache les données dans un Document protégé par mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [L’accès aux données dans des Documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Enregistrer des données](/visualstudio/data-tools/saving-data)  
  
  