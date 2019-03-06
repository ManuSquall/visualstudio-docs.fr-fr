---
title: 'Procédure : Mettre en cache les données pour une utilisation hors connexion ou sur un serveur'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bae12ea054c674e14da53fe60879c5466120d0a9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636513"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procédure : Mettre en cache les données pour une utilisation hors connexion ou sur un serveur
  Vous pouvez marquer un élément de données doit être mis en cache dans le document, afin qu’il soit disponible hors connexion. Cela rend également possible pour les données dans le document pour être manipulée par un autre code lorsque le document est stocké sur un serveur.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Vous pouvez marquer un élément de données doit être mis en cache lorsque l’élément de données est déclaré dans votre code, ou, si vous utilisez un <xref:System.Data.DataSet>, en définissant une propriété le **propriétés** fenêtre. Si vous mettez en cache un élément de données qui n’est pas un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>, assurez-vous qu’il remplit les critères de mise en cache dans le document. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).

> [!NOTE]
>  Jeux de données créés à l’aide de Visual Basic qui sont marqués comme **mises en cache** et **WithEvents** (y compris les jeux de données qui est déplacées de la **des Sources de données** fenêtre ou **Boîte à outils** qui ont le **CacheInDocument** propriété définie sur **True**) ont un trait de soulignement comme préfixe à leur nom dans le cache. Par exemple, si vous créez un dataset et nommez **clients**, le <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nom sera **_Clients** dans le cache. Lorsque vous utilisez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour accéder à cet élément mis en cache, vous devez spécifier **_Clients** au lieu de **clients**.

### <a name="to-cache-data-in-the-document-using-code"></a>En cache des données dans le document à l’aide de code

1.  Déclarez un champ public ou une propriété pour l’élément de données en tant que membre d’une classe d’élément hôte dans votre projet, tel que le `ThisDocumen`classe t dans un projet Word ou la `ThisWorkbook` classe dans un projet Excel.

2.  Appliquer le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au membre pour marquer l’élément de données à stocker dans le cache de données du document. L’exemple suivant applique cet attribut à une déclaration de champ pour un <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  Ajoutez du code pour créer une instance de l’élément de données et, le cas échéant, à charger à partir de la base de données.

     L’élément de données est chargé uniquement lorsqu’il est tout d’abord créé ; par la suite, le cache reste avec le document, vous devez écrire le code pour mettre à jour.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Pour mettre en cache un jeu de données dans le document à l’aide de la fenêtre Propriétés

1.  Ajouter le jeu de données au projet à l’aide des outils dans le concepteur Visual Studio, par exemple, en ajoutant une source de données à votre projet en utilisant le **des Sources de données** fenêtre.

2.  Créez une instance du jeu de données si vous ne pas déjà un et sélectionnez l’instance dans le concepteur.

3.  Dans le **propriétés** fenêtre, définissez la **CacheInDocument** propriété **True**.

     Pour plus d’informations, consultez [Properties in Office Projects](../vsto/properties-in-office-projects.md).

4.  Dans le **propriétés** fenêtre, définissez la **modificateurs** propriété **Public** (par défaut, il est **interne**).

## <a name="see-also"></a>Voir aussi
- [Données du cache](../vsto/caching-data.md)
- [Guide pratique pour Mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Guide pratique pour Cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)
- [Enregistrer des données](../data-tools/saving-data.md)
