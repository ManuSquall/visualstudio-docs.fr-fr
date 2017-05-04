---
title: "Acc&#232;s aux donn&#233;es des documents sur le serveur | Microsoft Docs"
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
  - "données (développement Office dans Visual Studio), accéder au serveur"
  - "accès aux données (développement Office dans Visual Studio)"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Acc&#232;s aux donn&#233;es des documents sur le serveur
  Vous pouvez programmer par rapport aux données d'une personnalisation au niveau du document sans devoir utiliser le modèle objet de Microsoft Office Word ou Microsoft Office Excel.  Cela signifie que vous pouvez accéder aux données contenues dans un document sur un serveur sur lequel Word ou Excel n'est pas installé.  Par exemple, un code sur un serveur \(dans une page [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], par exemple\) peut personnaliser les données d'un document et envoyer le document ainsi personnalisé à un utilisateur final.  Lorsque l'utilisateur final ouvre le document, le code de liaison de données dans l'assembly de solution lie les données personnalisées dans le document.  Cette opération est possible car les données du document sont séparées de l'interface utilisateur.  Pour plus d’informations, consultez [Données mises en cache dans des personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Mise en cache de données pour une utilisation sur un serveur  
 Pour mettre un objet de données en cache dans un document, marquez\-le avec l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> au moment du design ou utilisez la méthode `StartCaching` d'un élément hôte au moment de l'exécution.  Lorsque vous mettez en cache un objet de données dans un document, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sérialise l'objet dans une chaîne XML stockée dans le document.  Pour pouvoir être mis en cache, les objets doivent répondre à certains critères.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
 Le code côté serveur peut manipuler n'importe quel objet de données dans le cache de données.  Les contrôles liés aux instances de données en mémoire cache sont synchronisés avec l'interface utilisateur, afin que toutes les modifications côté serveur apportées aux données s'affichent automatiquement lorsque le document est ouvert sur le client.  
  
## Accès aux données du cache  
 Vous pouvez accéder aux données contenues dans le cache à partir d'applications en dehors de Microsoft Office, par exemple à partir d'une application console, d'une application Windows Forms ou d'une page Web.  L'application qui accède aux données en mémoire cache doit avoir le niveau de confiance totale ; une application Web qui dispose de la confiance partielle ne peut pas insérer, récupérer ou modifier des données mises en cache dans un document Office.  
  
 Le cache de données est accessible via une hiérarchie de collections exposées par la propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> de la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> :  
  
-   La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> retourne un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, qui contient toute les données en mémoire cache dans une personnalisation au niveau du document.  
  
-   Chaque <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contient un ou plusieurs objets <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>.  Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contient tous les objets de données en mémoire cache définis dans une seule classe.  
  
-   Chaque <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contient un ou plusieurs objets <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>.  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> représente un objet de données en mémoire cache unique.  
  
 L'exemple de code suivant montre comment accéder à une chaîne mise en cache dans la classe `Sheet1` d'un projet de classeur Excel.  Cet exemple de code fait partie d'un exemple plus complet fourni pour la méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## Modification des données du cache  
 Pour modifier un objet des données en mémoire cache, vous suivez généralement la procédure suivante :  
  
1.  Désérialisez la représentation XML de l'objet en mémoire cache dans une nouvelle instance de l'objet.  Vous pouvez accéder au XML à l'aide de la propriété <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> du <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> qui représente l'objet de données en mémoire cache.  
  
2.  Apportez les modifications nécessaires à cette copie.  
  
3.  Resérialisez l'objet modifié dans le cache de données à l'aide d'une des options suivantes :  
  
    -   Pour sérialiser automatiquement les modifications, utilisez la méthode <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>.  Cette méthode utilise le format **DiffGram** pour sérialiser le <xref:System.Data.DataSet>, le <xref:System.Data.DataTable> et les objets d'un groupe de données typé dans le cache de données.  Le format **DiffGram** garantit que les modifications apportées au cache de données dans un document hors connexion sont envoyées correctement au serveur.  
  
    -   Si vous souhaitez exécuter votre propre sérialisation des modifications apportées aux données mises en cache, vous pouvez écrire directement dans la propriété <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>.  Spécifiez le format **DiffGram** si vous utilisez <xref:System.Data.Common.DataAdapter> pour mettre à jour une base de données avec les modifications apportées aux données dans un groupe de données <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou typé.  Sinon, le <xref:System.Data.Common.DataAdapter> mettra à jour la base de données en ajoutant de nouvelles lignes au lieu de modifier des lignes existantes.  
  
### Modification de données sans désérialiser la valeur actuelle  
 Dans certains cas, vous pouvez souhaiter modifier la valeur de l'objet mis en cache sans désérialiser préalablement la valeur actuelle.  Vous pouvez par exemple procéder de la sorte si vous modifiez la valeur d'un objet de type simple, tel qu'une chaîne ou un nombre entier, ou si vous initialisez un <xref:System.Data.DataSet> mis en cache dans un document sur un serveur.  Dans ces cas\-là, vous pouvez utiliser la méthode <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> sans désérialiser en préalablement la valeur actuelle de l'objet mis en cache.  
  
 L'exemple de code suivant montre comment modifier la valeur d'une chaîne mise en cache dans la classe `Sheet1` d'un projet de classeur Excel.  Cet exemple de code fait partie d'un exemple plus complet fourni pour la méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### Modification de valeurs null dans le cache de données  
 Le cache de données ne stocke aucun objet ayant la valeur **null** lorsque le document est enregistré et fermé.  Cette limitation a plusieurs conséquences lorsque vous modifiez les données mises en cache :  
  
-   Si vous affectez la valeur **null** à un objet quelconque du cache de données, tous les objets du cache prendront automatiquement la valeur **null** à l'ouverture du document et l'ensemble du cache de données sera effacé lors de l'enregistrement et de la fermeture du document.  Autrement dit, tous les objets mis en cache seront supprimés du cache de données et la collection <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> sera vide.  
  
-   Si vous construisez une solution avec des objets **null** dans le cache de données et vous souhaitez initialiser ces objets à l'aide de la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> avant la première ouverture du document, vous devez veiller à initialiser tous les objets du cache de données.  Si vous initialisez uniquement certains objets, tous les objets prendront la valeur **null** à l'ouverture du document et l'ensemble du cache de données entier sera effacé lors de l'enregistrement et de la fermeture du document.  
  
## Accès aux groupes de données typées du cache  
 Si vous souhaitez accéder à la fois aux données d'un dataset typé d'une solution Office et d'une application non Office, telle qu'une application Windows Forms ou un projet [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], vous devez définir le groupe de données typé dans un assembly séparé, référencé dans les deux projets.  Si vous ajoutez le groupe de données typé à chaque projet à l'aide de l'**Assistant Configuration de source de données** ou du **Concepteur de DataSet**, le .NET Framework traitera les groupes de données typées dans les deux projets comme des types différents.  Pour plus d'informations sur la création de groupes de données typés, consultez [Comment : créer un groupe de données typé](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md).  
  
## Voir aussi  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Données mises en cache dans des personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md)  
  
  