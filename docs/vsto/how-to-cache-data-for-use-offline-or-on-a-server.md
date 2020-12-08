---
title: 'Procédure : mettre en cache des données pour une utilisation hors connexion ou sur un serveur'
description: Marquez un élément de données à mettre en cache dans le document, afin qu’il soit disponible hors connexion. Cela permet aux données du document d’être manipulées par un autre code.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: cefd4cd132e75f8ff622c8e0d809d317242c10f5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844320"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procédure : mettre en cache des données pour une utilisation hors connexion ou sur un serveur
  Vous pouvez marquer un élément de données à mettre en cache dans le document, afin qu’il soit disponible hors connexion. Cela permet également aux données du document d’être manipulées par un autre code lorsque le document est stocké sur un serveur.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Vous pouvez marquer un élément de données à mettre en cache lorsque l’élément de données est déclaré dans votre code, ou, si vous utilisez un <xref:System.Data.DataSet> , en définissant une propriété dans la fenêtre **Propriétés** . Si vous mettez en cache un élément de données qui n’est pas un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> , assurez-vous qu’il répond aux critères de mise en cache dans le document. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

> [!NOTE]
> Les jeux de données créés à l’aide de Visual Basic marqués comme **mis en cache** et **WithEvents** (y compris les datasets qui sont déplacés à partir de la fenêtre **sources de données** ou de la **boîte à outils** dont la propriété **CacheInDocument** a la valeur **true**) ont un trait de soulignement préfixé à leur nom dans le cache. Par exemple, si vous créez un DataSet et le nommez **Customers**, le <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nom sera **_Customers** dans le cache. Lorsque vous utilisez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour accéder à cet élément mis en cache, vous devez spécifier **_Customers** au lieu de **clients**.

### <a name="to-cache-data-in-the-document-using-code"></a>Pour mettre en cache des données dans le document à l’aide de code

1. Déclarez un champ public ou une propriété publique pour l’élément de données en tant que membre d’une classe d’élément hôte dans votre projet, tel que la `ThisDocumen` classe t dans un projet Word ou la `ThisWorkbook` classe dans un projet Excel.

2. Appliquez l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au membre pour marquer l’élément de données à stocker dans le cache de données du document. L’exemple suivant applique cet attribut à une déclaration de champ pour un <xref:System.Data.DataSet> .

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Ajoutez du code pour créer une instance de l’élément de données et, le cas échéant, pour le charger à partir de la base de données.

     L’élément de données est chargé uniquement lorsqu’il est créé pour la première fois ; par la suite, le cache reste avec le document et vous devez écrire un autre code pour le mettre à jour.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Pour mettre en cache un jeu de données dans le document à l’aide de l’Fenêtre Propriétés

1. Ajoutez le DataSet au projet à l’aide des outils du concepteur Visual Studio, par exemple, en ajoutant une source de données à votre projet à l’aide de la fenêtre **sources de données** .

2. Créez une instance du DataSet si vous n’en avez pas déjà un, puis sélectionnez l’instance dans le concepteur.

3. Dans la fenêtre **Propriétés** , affectez à la propriété **CacheInDocument** la **valeur true**.

     Pour plus d’informations, consultez [Propriétés dans les projets Office](../vsto/properties-in-office-projects.md).

4. Dans la fenêtre **Propriétés** , affectez à la propriété **Modifiers** la valeur **public** (par défaut, elle est **interne**).

## <a name="see-also"></a>Voir aussi
- [Données de cache](../vsto/caching-data.md)
- [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accéder aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)
- [Enregistrer les données](../data-tools/save-data-back-to-the-database.md)
