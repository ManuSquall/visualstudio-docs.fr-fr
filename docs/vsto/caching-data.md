---
title: "Mise en cache des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "données (développement Office dans Visual Studio), mettre en cache"
  - "mise en cache de données (développement Office dans Visual Studio)"
  - "mise en cache de données (développement Office dans Visual Studio), à propos de la mise en cache de données"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Mise en cache des donn&#233;es
  Vous pouvez mettre en cache des objets de données dans une personnalisation au niveau du document afin de pouvoir accéder aux données hors connexion ou sans ouvrir Microsoft Office Word ni Microsoft Office Excel.  Pour qu'un objet puisse être mis en cache, il doit avoir un type de données qui réponde à certaines spécifications.  De nombreux types de données courants du .NET Framework satisfont à ces exigences, notamment <xref:System.String>, <xref:System.Data.DataSet> et <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il y a deux façons d'ajouter un objet au cache de données :  
  
-   Pour ajouter un objet au cache de données lorsque la solution est construite, appliquez l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> à la déclaration de l'objet.  Pour plus d’informations, consultez [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Pour ajouter un objet par programmation au cache de données au moment de l'exécution, utilisez la méthode `StartCaching` d'un élément hôte, tel que les classes `ThisDocument` ou `ThisWorkbook`.  Pour plus d’informations, consultez [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Après avoir ajouté un objet au cache de données, vous pouvez accéder aux données en mémoire cache et les modifier sans avoir à démarrer Word ou Excel.  Pour plus d’informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Prérequis pour les objets de données à mettre en cache  
 Pour mettre en cache un objet de données dans votre solution, l'objet doit répondre aux conditions suivantes :  
  
-   doit être un champ public en lecture\/écriture ou une propriété d'un élément hôte, p. ex. : les classes `ThisDocument` ou `ThisWorkbook` ;  
  
-   ne doit pas être un indexeur ou autre propriété paramétrée.  
  
 De plus, l'objet de données doit être sérialisable par la classe <xref:System.Xml.Serialization.XmlSerializer>, ce qui signifie que le type de l'objet doit avoir les caractéristiques suivantes :  
  
-   doit être un type public ;  
  
-   doit avoir un constructeur public sans paramètres ;  
  
-   ne doit pas exécuter de code requérant des privilèges de sécurité supplémentaires ;  
  
-   doit exposer uniquement des propriétés publiques en lecture\/écriture \(les autres propriétés seront ignorées\) ;  
  
-   ne doit pas exposer de tableaux multidimensionnels \(les tableaux imbriqués sont acceptés\) ;  
  
-   ne doit pas retourner d'interfaces des propriétés et champs ;  
  
-   ne doit pas implémenter <xref:System.Collections.IDictionary> si une collection.  
  
 Lorsque vous mettez en cache un objet de données, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sérialise l'objet dans une chaîne XML stockée dans une *partie XML personnalisée* du document.  Pour plus d’informations, consultez [Vue d'ensemble des parties XML personnalisées](../vsto/custom-xml-parts-overview.md).  
  
## Limites de taille des données en mémoire cache  
 Il existe des limites à la quantité de données et à la taille des objets que vous pouvez ajouter au cache de données d'un document.  Si vous dépassez ces limites, l'application peut se fermer de façon inattendue au moment d'enregistrer les données dans le cache.  
  
 Pour ne pas dépasser ces limites, suivez les indications suivantes :  
  
-   N'ajoutez pas au cache de données des objets dont la taille est supérieure à 10 Mo.  
  
-   N'ajoutez pas au cache des données dont la taille totale dépasse 100 Mo dans un même document.  
  
 Il s'agit de valeurs approximatives.  Les limites exactes dépendent de plusieurs facteurs, notamment de la mémoire vive disponible et du nombre de processus en cours d'exécution.  
  
## Contrôle du comportement des objets mis en cache  
 Pour mieux contrôler le comportement d'un objet mis en cache, vous pouvez implémenter l'interface <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> sur le type de l'objet mis en cache.  Par exemple, vous pouvez implémenter cette interface si vous souhaitez contrôler la manière dont l'utilisateur est informé d'une modification de l'objet.  Pour obtenir des exemples de code qui montrent comment implémenter <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, consultez la classe `ControlCollection` dans les exemples de contrôles dynamiques Word et Excel dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Apport de modifications persistantes à des données en mémoire cache dans des documents protégés par mot de passe  
 Si vous mettez en cache des objets de données dans un document protégé par un mot de passe, les modifications apportées aux données en mémoire cache ne seront pas enregistrées.  Vous pouvez enregistrer les modifications des données en mémoire cache en substituant deux méthodes.  Substituez ces méthodes afin de supprimer temporairement la protection lorsque le document est enregistré, puis réappliquez la protection une fois l'enregistrement terminé.  
  
 Pour plus d’informations, consultez [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## Prévention des pertes de données lors de l'ajout de valeurs Null au cache de données  
 Lorsque vous ajoutez des objets au cache de données, tous les objets mis en cache doivent être initialisés à une valeur non **null** avant que le document ne soit enregistré et fermé.  Si un objet mis en cache a une valeur **null** lorsque le document est enregistré puis fermé, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] supprimera automatiquement du cache de données tous les objets mis en cache.  
  
 Si vous ajoutez un objet possédant une valeur **null** au cache de données en utilisant l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> au moment du design, vous pouvez utiliser la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour initialiser les objets de données en mémoire cache avant que le document ne soit ouvert.  Ceci s'avère utile si vous souhaitez initialiser les données en mémoire cache sur un serveur dépourvu de Word ou Excel, avant que le document ne soit ouvert par un utilisateur final.  Pour plus d’informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Voir aussi  
 [Comment : mettre en cache des données pour une utilisation hors connexion ou sur un serveur](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Procédure pas à pas : création d'une relation maître&#47;détail à l'aide d'un groupe de données mis en cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  