---
title: Mise en cache de données | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 094a4e6c639007fcf09ce28f0be2e398b8245858
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="caching-data"></a>Mise en cache des données
  Vous pouvez mettre en cache les objets de données dans une personnalisation au niveau du document afin que les données soient accessibles en mode hors connexion ou sans ouvrir Microsoft Office Word ou Microsoft Office Excel. Pour mettre en cache un objet, l’objet doit avoir un type de données qui répond à certaines exigences. Nombreux types de données courants dans le .NET Framework répondent à ces exigences, y compris <xref:System.String>, <xref:System.Data.DataSet>, et <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il existe deux façons d’ajouter un objet au cache de données :  
  
-   Pour ajouter un objet au cache de données lorsque la solution est construite, appliquez le <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> à la déclaration de l’objet d’attribut. Pour plus d’informations, consultez [Comment : les données du Cache pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Pour ajouter par programmation un objet au cache de données en cours d’exécution, utilisez la `StartCaching` (méthode) d’un ordinateur hôte de l’élément, telles que la `ThisDocument` ou `ThisWorkbook` classes. Pour plus d’informations, consultez [Comment : mettre en Cache par programmation une Source de données dans un Document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Après avoir ajouté un objet au cache de données, vous pouvez accéder et modifier les données mises en cache sans démarrer Word ou Excel. Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Configuration requise pour les objets de données doit être mis en cache  
 Pour mettre en cache un objet de données dans votre solution, l’objet doit respecter ces conditions :  
  
-   Être d’un champ public de lecture/écriture ou une propriété d’un élément hôte, tel que le `ThisDocument` ou `ThisWorkbook` classes.  
  
-   Ne pas être un indexeur ou autre propriété paramétrée.  
  
 En outre, l’objet de données doit être sérialisable par le <xref:System.Xml.Serialization.XmlSerializer> (classe), ce qui signifie que le type de l’objet doit avoir les caractéristiques :  
  
-   Être un type public.  
  
-   Posséder un constructeur public sans paramètres.  
  
-   Pas d’exécuter du code qui requiert des privilèges de sécurité supplémentaires.  
  
-   Exposent uniquement en lecture/écriture des propriétés publiques (les autres propriétés seront ignorées).  
  
-   Exposez pas des tableaux multidimensionnels (tableaux imbriqués sont acceptés).  
  
-   Ne pas retourner d’interfaces des propriétés et champs.  
  
-   Implémente pas <xref:System.Collections.IDictionary> si une collection.  
  
 Lorsque vous mettez en cache un objet de données, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sérialise l’objet dans une chaîne XML qui est stockée dans un *partie XML personnalisée* dans le document. Pour plus d'informations, consultez [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Limites de taille des données mises en cache  
 Il existe certaines limites relatives à la quantité totale de données, que vous pouvez ajouter au cache de données dans un document et la taille des objets dans le cache de données. Si vous dépassez ces limites, l’application risquent de se fermer inopinément lorsque les données sont enregistrées dans le cache de données.  
  
 Pour éviter ces limites, suivez ces instructions :  
  
-   N’ajoutez pas de n’importe quel objet supérieure à 10 Mo au cache de données.  
  
-   N’ajoutez pas plus de 100 Mo de données total pour le cache de données dans un document unique.  
  
 Il s’agit des valeurs approximatives. Les limites exactes dépendent de plusieurs facteurs, notamment la mémoire vive disponible et le nombre de processus en cours d’exécution.  
  
## <a name="controlling-the-behavior-of-cached-objects"></a>Contrôler le comportement des objets mis en cache  
 Pour mieux contrôler le comportement d’un objet mis en cache, vous pouvez implémenter la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface sur le type de l’objet mis en cache. Par exemple, vous pouvez implémenter cette interface si vous souhaitez contrôler la façon dont l’utilisateur est averti lorsque l’objet a été modifiée. Pour obtenir des exemples de code qui montrent comment implémenter <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, consultez la `ControlCollection` classe dans l’exemple de contrôles dynamiques Excel et Word dynamique dans [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persisting-changes-to-cached-data-in-password-protected-documents"></a>Rendre persistantes les modifications de données mises en cache dans les Documents protégés par mot de passe  
 Si vous mettez en cache des objets de données dans un document est protégé par un mot de passe, les modifications apportées aux données mises en cache ne sont pas enregistrées. Vous pouvez enregistrer les modifications aux données mises en cache en substituant deux méthodes. Substituer ces méthodes pour supprimer temporairement la protection lorsque le document est enregistré et réappliquez la protection une fois l’opération est terminée.  
  
 Pour plus d’informations, consultez [Comment : Cache des données dans un Document protégé](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="preventing-data-loss-when-adding-null-values-to-the-data-cache"></a>Prévention des pertes de données lors de l’ajout de valeurs Null dans le Cache de données  
 Lorsque vous ajoutez des objets au cache de données, tous les objets mis en cache doivent être initialisés à une non -**null** valeur avant que le document est enregistré puis fermé. Si un objet mis en cache a un **null** valeur lorsque le document est enregistré puis fermé, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] supprimera automatiquement tous les objets mis en cache à partir du cache de données.  
  
 Si vous ajoutez un objet avec un **null** valeur au cache de données à l’aide de la <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribut au moment du design, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe pour initialiser les données mises en cache des objets avant l’ouverture du document. Cela est utile si vous souhaitez initialiser les données mises en cache sur un serveur sans Word ou Excel, avant que le document est ouvert par un utilisateur final. Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : mettre en Cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Comment : mettre en Cache par programmation une Source de données dans un Document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Comment : mettre en Cache les données dans un Document protégé par mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Procédure pas à pas : création d’une relation maître/détail à l’aide d’un groupe de données mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  