---
title: Accéder aux données dans des documents sur le serveur
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
ms.openlocfilehash: d12c8168ef01dd3a38616af4f9dab2c38662bfff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102575"
---
# <a name="access-data-in-documents-on-the-server"></a>Accéder aux données dans des documents sur le serveur
  Vous pouvez programmer les données dans une personnalisation au niveau du document sans avoir à utiliser le modèle objet de Microsoft Office Word ou Microsoft Office Excel. Cela signifie que vous pouvez accéder à des données contenues dans un document sur un serveur qui n’a pas de Word ou Excel est installé. Par exemple, le code sur un serveur (par exemple, dans un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] page) peut personnaliser les données dans un document et envoyer le document personnalisé à un utilisateur final. Lorsque l’utilisateur final ouvre le document, le code de liaison de données dans l’assembly de solution lie les données personnalisées dans le document. Cela est possible, car les données dans le document sont séparées de l’interface utilisateur. Pour plus d’informations, consultez [mis en cache des données dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Données du cache pour une utilisation sur un serveur
 Pour mettre en cache un objet de données dans un document, marquez-le avec le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au moment du design, ou utiliser le `StartCaching` méthode d’un élément hôte lors de l’exécution. Lorsque vous mettez en cache un objet de données dans un document, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sérialise l’objet dans une chaîne XML qui est stockée dans le document. Objets doivent remplir certaines conditions pour être éligible à la mise en cache. Pour plus d’informations, consultez [mettre en Cache données](../vsto/caching-data.md).

 Code côté serveur peut manipuler d’objets de données dans le cache de données. Contrôles liés aux instances de données mises en cache sont synchronisés avec l’interface utilisateur, afin que toutes les modifications côté serveur qui sont apportées aux données s’affichent automatiquement lorsque le document est ouvert sur le client.

## <a name="access-data-in-the-cache"></a>Accéder aux données dans le cache
 Vous pouvez accéder des données dans le cache à partir d’applications en dehors d’Office, par exemple à partir d’une application console, une application Windows Forms ou une page Web. L’application qui accède aux données mises en cache doit avoir une confiance totale ; une application Web avec confiance partielle ne peut pas insérer, récupérer ou modifier des données qui sont mis en cache dans un document Office.

 Le cache de données est accessible via une hiérarchie de collections qui est exposée par le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propriété de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe :

- Le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propriété retourne un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, qui contient toutes les données mises en cache dans une personnalisation au niveau du document.

- Chaque <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contient un ou plusieurs <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> objets. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contient tous les objets de données mises en cache qui sont définis dans une classe unique.

- Chaque <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contient un ou plusieurs <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> objets. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> représente un objet de données mis en cache.

  L’exemple de code suivant montre comment accéder à une chaîne mise en cache dans le `Sheet1` classe d’un projet de classeur Excel. Cet exemple fait partie d’un exemple plus complet fourni pour le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> (méthode).

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modifier des données dans le cache
 Pour modifier un objet de données mises en cache, vous procédez généralement comme suit :

1. Désérialiser la représentation XML de l’objet mis en cache dans une nouvelle instance de l’objet. Vous pouvez accéder aux données XML à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propriété de la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> qui représente l’objet de données mises en cache.

2. Apportez les modifications à cette copie.

3. Pour sérialiser l’objet modifié dans le cache de données en utilisant l’une des options suivantes :

    - Si vous souhaitez sérialiser automatiquement les modifications, utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> (méthode). Cette méthode utilise la **DiffGram** format de sérialisation <xref:System.Data.DataSet>, <xref:System.Data.DataTable>et des objets de jeu de données typé dans le cache de données. Le **DiffGram** format garantit que les modifications apportées au cache de données dans un document en mode hors connexion sont envoyées correctement au serveur.

    - Si vous souhaitez exécuter votre propre sérialisation des modifications apportées aux données mises en cache, vous pouvez écrire directement dans le <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> propriété. Spécifiez le **DiffGram** mettre en forme si vous utilisez un <xref:System.Data.Common.DataAdapter> pour mettre à jour une base de données avec les modifications apportées aux données dans un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou le dataset typé. Sinon, le <xref:System.Data.Common.DataAdapter> met à jour la base de données en ajoutant de nouvelles lignes au lieu de modifier les lignes existantes.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modifier des données sans désérialiser la valeur actuelle
 Dans certains cas, vous souhaiterez modifier la valeur de l’objet mis en cache sans désérialiser la valeur actuelle en premier. Par exemple, vous pouvez le faire si vous modifiez la valeur d’un objet qui a un type simple, tel qu’une chaîne ou un entier, ou si vous initialisez une mise en cache <xref:System.Data.DataSet> dans un document sur un serveur. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> méthode sans désérialiser la valeur actuelle de l’objet mis en cache en premier.

 L’exemple de code suivant montre comment modifier la valeur d’une chaîne mise en cache dans le `Sheet1` classe d’un projet de classeur Excel. Cet exemple fait partie d’un exemple plus complet fourni pour le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> (méthode).

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modifier les valeurs null dans le cache de données
 Le cache de données ne stocke pas les objets qui ont la valeur **null** lorsque le document est enregistré et fermé. Cette limitation a plusieurs conséquences lorsque vous modifiez les données mises en cache :

- Si vous définissez n’importe quel objet dans le cache de données à la valeur **null**, tous les objets dans le cache de données seront automatiquement défini sur **null** lorsque le document est ouvert, et le cache de données entier sera effacé lorsque le document est enregistré puis fermé. Autrement dit, tous les objets mis en cache seront supprimés du cache de données et le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> collection sera vide.

- Si vous générez une solution avec **null** objets dans le cache de données et que vous souhaitez initialiser ces objets à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe avant que le document est ouvert pour la première fois, vous devez vous assurer que vous initialisez tous les objets dans le cache de données. Si vous initialisez uniquement certains objets, tous les objets définira sur **null** lorsque le document est ouvert et le cache de données entier sera effacé lorsque le document est enregistré et fermé.

## <a name="access-typed-datasets-in-the-cache"></a>Accès aux datasets typés dans le cache
 Si vous souhaitez accéder aux données dans un dataset typé à la fois à partir d’une solution Office et à partir d’une application en dehors d’Office, telle qu’une application Windows Forms ou une [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projet, vous devez définir le dataset typé dans un assembly distinct qui est référencé dans les deux projets. Si vous ajoutez le dataset typé à chaque projet à l’aide de la **Configuration de Source de données** Assistant ou la **Concepteur de Dataset**, le .NET Framework traite les datasets typés dans les deux projets comme des types différents . Pour plus d’informations sur la création de datasets typés, consultez [créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)
- [Données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md)