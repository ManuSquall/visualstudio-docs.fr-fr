---
title: Données de cache
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62939413"
---
# <a name="cache-data"></a>Données de cache
  Vous pouvez mettre en cache des objets de données dans une personnalisation au niveau du document afin que les données soient accessibles hors connexion ou sans ouvrir Microsoft Office Word ou Microsoft Office Excel. Pour mettre en cache un objet, l’objet doit avoir un type de données qui répond à certaines exigences. De nombreux types de données courants dans le .NET Framework répondent à ces exigences, notamment <xref:System.String> , <xref:System.Data.DataSet> et <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Il existe deux façons d’ajouter un objet au cache de données :

- Pour ajouter un objet au cache de données lors de la génération de la solution, appliquez l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut à la déclaration de l’objet. Pour plus d’informations, consultez [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Pour ajouter par programmation un objet au cache de données au moment de l’exécution, utilisez la `StartCaching` méthode d’un élément hôte, telle que `ThisDocument` les `ThisWorkbook` classes ou. Pour plus d’informations, consultez [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Après avoir ajouté un objet au cache de données, vous pouvez accéder aux données mises en cache et les modifier sans démarrer Word ou Excel. Pour plus d’informations, consultez [accéder aux données dans les documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Conditions requises pour les objets de données à mettre en cache
 Pour mettre en cache un objet de données dans votre solution, l’objet doit remplir les conditions suivantes :

- Doit être un champ ou une propriété publique en lecture/écriture d’un élément hôte, tel que les `ThisDocument` `ThisWorkbook` classes ou.

- Il ne s’agit pas d’un indexeur ou d’une autre propriété paramétrée.

  En outre, l’objet de données doit être sérialisable par la <xref:System.Xml.Serialization.XmlSerializer> classe, ce qui signifie que le type de l’objet doit présenter les caractéristiques suivantes :

- Être un type public.

- Avoir un constructeur public sans paramètres.

- N’exécutez pas de code nécessitant des privilèges de sécurité supplémentaires.

- Exposez uniquement les propriétés publiques en lecture/écriture (les autres propriétés seront ignorées).

- N’exposez pas les tableaux multidimensionnels (les tableaux imbriqués sont acceptés).

- Ne retourne pas les interfaces des propriétés et des champs.

- Ne pas implémenter <xref:System.Collections.IDictionary> si une collection.

  Lorsque vous mettez en cache un objet de données, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sérialise l’objet dans une chaîne XML stockée dans une *partie XML personnalisée* dans le document. Pour plus d’informations, consultez [vue d’ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Limites de taille des données mises en cache
 Il existe certaines limites à la quantité totale de données que vous pouvez ajouter au cache de données dans un document, ainsi qu’à la taille d’un objet individuel dans le cache de données. Si vous dépassez ces limites, l’application peut se fermer de manière inattendue lors de l’enregistrement des données dans le cache de données.

 Pour éviter ces limites, suivez ces instructions :

- N’ajoutez pas d’objets d’une taille supérieure à 10 Mo dans le cache de données.

- N’ajoutez pas plus de 100 Mo de données totales au cache de données dans un seul document.

  Il s’agit de valeurs approximatives. Les limites exactes dépendent de plusieurs facteurs, notamment la quantité de mémoire disponible et le nombre de processus en cours d’exécution.

## <a name="control-the-behavior-of-cached-objects"></a>Contrôler le comportement des objets mis en cache
 Pour mieux contrôler le comportement d’un objet mis en cache, vous pouvez implémenter l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface sur le type de l’objet mis en cache. Par exemple, vous pouvez implémenter cette interface si vous souhaitez contrôler la façon dont l’utilisateur est averti lorsque l’objet a été modifié. Pour obtenir des exemples de code qui montrent comment implémenter <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> , consultez la `ControlCollection` classe dans l’exemple contrôles dynamiques Excel et exemples de contrôles dynamiques Word dans [exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Conserver les modifications apportées aux données mises en cache dans les documents protégés par mot de passe
 Si vous mettez en cache des objets de données dans un document protégé par un mot de passe, les modifications apportées aux données mises en cache ne sont pas enregistrées. Vous pouvez enregistrer les modifications apportées aux données mises en cache en remplaçant deux méthodes. Remplacez ces méthodes pour supprimer temporairement la protection lorsque le document est enregistré, puis réappliquez la protection une fois l’opération d’enregistrement terminée.

 Pour plus d’informations, consultez [Comment : mettre en cache des données dans un document protégé par mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Empêcher la perte de données lors de l’ajout de valeurs NULL au cache de données
 Lorsque vous ajoutez des objets au cache de données, tous les objets mis en cache doivent être initialisés à une valeur non**null** avant que le document ne soit enregistré et fermé. Si un objet mis en cache a une valeur **null** lorsque le document est enregistré et fermé, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] supprime automatiquement tous les objets mis en cache du cache de données.

 Si vous ajoutez un objet avec une valeur **null** au cache de données à l’aide de l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au moment du design, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour initialiser les objets de données en mémoire cache avant l’ouverture du document. Cela est utile si vous souhaitez initialiser les données mises en cache sur un serveur sans que Word ou Excel soit installé, avant que le document ne soit ouvert par un utilisateur final. Pour plus d’informations, consultez [accéder aux données dans les documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Voir aussi
- [Procédure : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Procédure pas à pas : créer une relation de détail maître à l’aide d’un DataSet mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
