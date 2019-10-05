---
title: Accéder aux données des documents sur le serveur
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ab033120c0913bbae33458c5a2d0b53972364581
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255764"
---
# <a name="access-data-in-documents-on-the-server"></a>Accéder aux données des documents sur le serveur
  Vous pouvez programmer des données dans une personnalisation au niveau du document sans avoir à utiliser le modèle objet de Microsoft Office Word ou Microsoft Office Excel. Cela signifie que vous pouvez accéder aux données contenues dans un document sur un serveur sur lequel Word ou Excel n’est pas installé. Par exemple, le code d’un serveur (par exemple, dans [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] une page) peut personnaliser les données d’un document et envoyer le document personnalisé à un utilisateur final. Lorsque l’utilisateur final ouvre le document, le code de liaison de données dans l’assembly de solution lie les données personnalisées au document. Cela est possible parce que les données du document sont séparées de l’interface utilisateur. Pour plus d’informations, consultez [données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Mettre en cache les données pour une utilisation sur un serveur
 Pour mettre en cache un objet de données dans un document, marquez-le avec l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au moment du design, ou utilisez la `StartCaching` méthode d’un élément hôte au moment de l’exécution. Lorsque vous mettez en cache un objet de données dans un [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] document, le sérialise l’objet dans une chaîne XML stockée dans le document. Les objets doivent répondre à certaines exigences pour être éligibles à la mise en cache. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

 Le code côté serveur peut manipuler tous les objets de données dans le cache de données. Les contrôles liés aux instances de données mises en cache sont synchronisés avec l’interface utilisateur, de sorte que toutes les modifications côté serveur apportées aux données s’affichent automatiquement lorsque le document est ouvert sur le client.

## <a name="access-data-in-the-cache"></a>Accéder aux données dans le cache
 Vous pouvez accéder aux données du cache à partir d’applications en dehors d’Office, par exemple à partir d’une application console, d’une application Windows Forms ou d’une page Web. L’application qui accède aux données mises en cache doit avoir une confiance totale ; une application Web qui a une confiance partielle ne peut pas insérer, récupérer ou modifier les données mises en cache dans un document Office.

 Le cache de données est accessible par le biais d’une hiérarchie de collections qui <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> sont exposées par <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> la propriété de la classe :

- La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propriété retourne un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, qui contient toutes les données mises en cache dans une personnalisation au niveau du document.

- Chaque <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contient un ou plusieurs <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objets. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objet contient tous les objets de données mis en cache qui sont définis dans une classe unique.

- Chaque <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contient un ou plusieurs <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> objets. <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Représente un objet de données mis en cache unique.

  L’exemple de code suivant montre comment accéder à une chaîne mise en cache `Sheet1` dans la classe d’un projet de classeur Excel. Cet exemple fait partie d’un exemple plus complet fourni pour la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> méthode.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modifier des données dans le cache
 Pour modifier un objet de données mis en cache, vous devez généralement effectuer les étapes suivantes :

1. Désérialisez la représentation XML de l’objet mis en cache dans une nouvelle instance de l’objet. Vous pouvez accéder au XML à l’aide <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> de la propriété du qui représente l’objet de données mis en cache.

2. Apportez les modifications à cette copie.

3. Sérialisez de nouveau l’objet modifié dans le cache de données en utilisant l’une des options suivantes :

    - Si vous souhaitez sérialiser automatiquement les modifications, utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> méthode. Cette méthode utilise le format **DiffGram** pour sérialiser <xref:System.Data.DataSet>les <xref:System.Data.DataTable>objets DataSet typés, et dans le cache de données. Le format **DiffGram** garantit que les modifications apportées au cache de données dans un document hors connexion sont correctement envoyées au serveur.

    - Si vous souhaitez effectuer votre propre sérialisation pour les modifications apportées aux données mises en cache, vous pouvez écrire <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> directement dans la propriété. Spécifiez le format **DiffGram** si vous utilisez <xref:System.Data.Common.DataAdapter> un pour mettre à jour une base de données avec les <xref:System.Data.DataSet>modifications apportées aux données dans un DataSet typé, <xref:System.Data.DataTable>ou. Dans le cas <xref:System.Data.Common.DataAdapter> contraire, le met à jour la base de données en ajoutant de nouvelles lignes au lieu de modifier les lignes existantes.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modifier des données sans désérialiser la valeur actuelle
 Dans certains cas, vous souhaiterez peut-être modifier la valeur de l’objet mis en cache sans désérialiser au préalable la valeur actuelle. Par exemple, vous pouvez le faire si vous modifiez la valeur d’un objet qui a un type simple, tel qu’une chaîne ou un entier, ou si vous initialisez un mis en cache <xref:System.Data.DataSet> dans un document sur un serveur. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> méthode sans désérialiser au préalable la valeur actuelle de l’objet mis en cache.

 L’exemple de code suivant montre comment modifier la valeur d’une chaîne mise en cache dans `Sheet1` la classe d’un projet de classeur Excel. Cet exemple fait partie d’un exemple plus complet fourni pour la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> méthode.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modifier les valeurs NULL dans le cache de données
 Le cache de données ne stocke pas les objets qui ont la valeur **null** lorsque le document est enregistré et fermé. Cette limitation a plusieurs conséquences lorsque vous modifiez les données mises en cache :

- Si vous affectez à un objet du cache de données la valeur **null**, tous les objets du cache de données sont automatiquement définis sur **null** lorsque le document est ouvert, et l’intégralité du cache de données est effacée lorsque le document est enregistré et fermé. Autrement dit, tous les objets mis en cache sont supprimés du cache de données, et la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> collection est vide.

- Si vous générez une solution avec des objets **null** dans le cache de données et que vous souhaitez initialiser ces objets <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> à l’aide de la classe avant que le document ne soit ouvert pour la première fois, vous devez vous assurer que vous initialisez tous les objets dans le cache de données. Si vous initialisez uniquement certains objets, tous les objets ont la valeur **null** lorsque le document est ouvert, et l’intégralité du cache de données est effacée lorsque le document est enregistré et fermé.

## <a name="access-typed-datasets-in-the-cache"></a>Accéder à des datasets typés dans le cache
 Si vous souhaitez accéder aux données d’un DataSet typé à la fois à partir d’une solution Office et d’une application extérieure à Office, par exemple une application [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Windows Forms ou un projet, vous devez définir le DataSet typé dans un assembly distinct qui est référencé dans les deux projet. Si vous ajoutez le DataSet typé à chaque projet à l’aide de l’Assistant **configuration de source de données** ou de la **Concepteur de DataSet**, le .NET Framework traitera les datasets typés dans les deux projets comme des types différents. Pour plus d’informations sur la création de datasets typés, consultez [créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Accéder aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)
- [Données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md)