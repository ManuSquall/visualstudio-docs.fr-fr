---
title: Données du cache
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939413"
---
# <a name="cache-data"></a>Données du cache
  Vous pouvez mettre en cache les objets de données dans une personnalisation au niveau du document afin que les données sont accessibles en mode hors connexion ou sans ouvrir Microsoft Office Word ou Microsoft Office Excel. Pour mettre en cache un objet, l’objet doit avoir un type de données qui répond à certaines exigences. Nombreux types de données courants dans le .NET Framework répondent à ces exigences, y compris <xref:System.String>, <xref:System.Data.DataSet>, et <xref:System.Data.DataTable>.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Il existe deux façons d’ajouter un objet au cache de données :

- Pour ajouter un objet au cache de données lorsque la solution est générée, appliquez le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> à la déclaration de l’objet d’attribut. Pour plus d'informations, voir [Procédure : Mettre en cache les données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Pour ajouter par programme un objet au cache de données en cours d’exécution, utilisez la `StartCaching` (méthode) d’un hôte de l’élément, tel que le `ThisDocument` ou `ThisWorkbook` classes. Pour plus d'informations, voir [Procédure : Mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Une fois que vous ajoutez un objet au cache de données, vous pouvez accéder et modifier les données mises en cache sans démarrer Word ou Excel. Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Configuration requise pour les objets de données doit être mis en cache
 Pour mettre en cache un objet de données dans votre solution, l’objet doit répondre à ces exigences :

- Être un champ public en lecture/écriture ou une propriété d’un élément hôte, tel que le `ThisDocument` ou `ThisWorkbook` classes.

- Ne pas être un indexeur ou autre propriété paramétrée.

  En outre, l’objet de données doit être sérialisable par le <xref:System.Xml.Serialization.XmlSerializer> (classe), ce qui signifie que le type de l’objet doit présenter ces caractéristiques :

- Être un type public.

- Avoir un constructeur public sans paramètres.

- N’exécute pas de code qui requiert des privilèges de sécurité supplémentaire.

- Exposent uniquement en lecture/écriture des propriétés publiques (les autres propriétés seront ignorées).

- Pas exposer des tableaux multidimensionnels (les tableaux imbriqués sont acceptés).

- Ne pas retourner d’interfaces à partir des propriétés et champs.

- Pas implémenter <xref:System.Collections.IDictionary> si une collection.

  Lorsque vous mettez en cache un objet de données, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sérialise l’objet dans une chaîne XML qui est stockée dans un *partie XML personnalisée* dans le document. Pour plus d’informations, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Limites de taille des données mises en cache
 Il existe certaines limites à la quantité totale de données que vous pouvez ajouter au cache de données dans un document et à la taille des objets dans le cache de données. Si vous dépassez ces limites, l’application peut fermer de façon inattendue lorsque les données sont enregistrées dans le cache de données.

 Pour éviter ces limites, suivez ces instructions :

- N’ajoutez pas de n’importe quel objet supérieure à 10 Mo au cache de données.

- N’ajoutez pas plus de 100 Mo de données total pour le cache de données dans un document unique.

  Il s’agit des valeurs approximatives. Les limites exactes dépendent de plusieurs facteurs, notamment la mémoire vive disponible et le nombre de processus en cours d’exécution.

## <a name="control-the-behavior-of-cached-objects"></a>Contrôler le comportement des objets mis en cache
 Pour mieux contrôler le comportement d’un objet mis en cache, vous pouvez implémenter la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface sur le type de l’objet mis en cache. Par exemple, vous pouvez implémenter cette interface si vous souhaitez contrôler la façon dont l’utilisateur est averti lorsque l’objet a été modifié. Pour obtenir des exemples de code qui montrent comment implémenter <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, consultez le `ControlCollection` classe dans l’exemple de contrôles dynamiques Excel et Word dynamique dans [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Conserver les modifications apportées aux données mises en cache dans les documents protégés par mot de passe
 Si vous mettez en cache des objets de données dans un document est protégé par un mot de passe, les modifications apportées aux données mises en cache ne sont pas enregistrées. Vous pouvez enregistrer des modifications aux données mises en cache en remplaçant les deux méthodes. Substituer ces méthodes pour supprimer temporairement la protection lorsque le document est enregistré et puis réappliquer la protection après l’enregistrement l’opération est terminée.

 Pour plus d'informations, voir [Procédure : Mettre en cache les données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Éviter la perte de données lors de l’ajout de valeurs null au cache de données
 Lorsque vous ajoutez des objets au cache de données, tous les objets mis en cache doivent être initialisé à une non -**null** valeur avant que le document est enregistré et fermé. Si un objet mis en cache a un **null** valeur lorsque le document est enregistré puis fermé, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] supprimera automatiquement tous les objets mis en cache à partir du cache de données.

 Si vous ajoutez un objet avec un **null** valeur au cache de données à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au moment du design, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour initialiser les données mises en cache des objets avant que le document est ouvert. Cela est utile si vous souhaitez initialiser les données mises en cache sur un serveur sans Word ou Excel, avant que le document est ouvert par un utilisateur final. Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Mettre en cache les données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Guide pratique pour Mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Guide pratique pour Cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Procédure pas à pas : Créer une relation maître/détail à l’aide d’un dataset mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
