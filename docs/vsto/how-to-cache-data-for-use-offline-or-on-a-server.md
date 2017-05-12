---
title: "Comment&#160;: mettre en cache des donn&#233;es pour une utilisation hors connexion ou sur un serveur"
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
  - "mise en cache de données (développement Office dans Visual Studio), utilisation hors connexion"
  - "mise en cache de données (développement Office dans Visual Studio), utilisation du serveur"
  - "groupes de données (développement Office dans Visual Studio), mettre en cache"
  - "applications Office (développement Office dans Visual Studio), données"
  - "données hors connexion (développement Office dans Visual Studio)"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Comment&#160;: mettre en cache des donn&#233;es pour une utilisation hors connexion ou sur un serveur
  Vous pouvez marquer un élément de données à mettre en cache dans le document, afin qu'il soit disponible hors connexion.  Cela permet également la manipulation des données du document par un autre code lorsque le document est stocké sur un serveur.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Vous pouvez marquer un élément de données à mettre en cache lorsque cet élément est déclaré dans votre code, ou, si vous utilisez <xref:System.Data.DataSet>, en définissant une propriété dans la fenêtre **Propriétés**.  Si vous mettez en cache un élément de données qui n'est pas <xref:System.Data.DataSet> ni <xref:System.Data.DataTable>, assurez\-vous qu'il réponde aux critères de mise en cache dans le document.  Pour plus d’informations, consultez [Mise en cache des données](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Les groupes de données créés à l'aide de Visual Basic et marqués comme **Cached** et **WithEvents** \(notamment les groupes de données déplacés à partir de la fenêtre **Sources de données** ou de la **Boîte à outils** et dont la propriété **CacheInDocument** a la valeur **True**\) ont un trait de soulignement comme préfixe à leur nom dans le cache.  Par exemple, si vous créez un groupe de données et lui attribuez le nom Clients, le nom <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> sera \_Clients dans le cache.  Lorsque vous utilisez <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour accéder à cet élément mis en cache, vous devez spécifier \_Clients au lieu de Clients.  
  
### Pour mettre en cache des données dans le document à l'aide du code  
  
1.  Déclarez un champ public ou une propriété publique pour l'élément de données en tant que membre d'une classe d'élément hôte dans votre projet, tel que la classe `ThisDocument` dans un projet Word ou la classe `ThisWorkbook` dans un projet Excel.  
  
2.  Appliquez l'attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> au membre pour marquer l'élément de données à stocker dans le cache de données du document.  L'exemple suivant applique cet attribut à une déclaration de champ pour <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  Ajoutez du code pour créer une instance de l'élément de données et, le cas échéant, la charger à partir de la base de données.  
  
     L'élément de données est uniquement chargé lors de sa création initiale ; ensuite, le cache est conservé avec le document et vous devez écrire un autre code pour le mettre à jour.  
  
### Pour mettre en cache un groupe de données dans le document à l'aide de la fenêtre Propriétés  
  
1.  Ajoutez le groupe de données au projet à l'aide des outils dans le concepteur Visual Studio, par exemple, en ajoutant une source de données à votre projet à l'aide de la fenêtre **Sources de données**.  
  
2.  Créez une instance du groupe de données si vous n'en possédez pas déjà une, et sélectionnez l'instance dans le concepteur.  
  
3.  Dans la fenêtre **Propriétés**, affectez à la propriété **CacheInDocument** la valeur **True**.  
  
     Pour plus d’informations, consultez [Propriétés dans les projets Office](../vsto/properties-in-office-projects.md).  
  
4.  Dans la fenêtre **Propriétés**, affectez la valeur **Public** à la propriété **Modifiers** \(la valeur par défaut est **Internal**\).  
  
## Voir aussi  
 [Mise en cache des données](../vsto/caching-data.md)   
 [Comment : mettre en cache par programmation une source de données dans un document Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Comment : mettre en cache des données dans un document protégé par un mot de passe](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Enregistrement des données](../data-tools/saving-data.md)  
  
  