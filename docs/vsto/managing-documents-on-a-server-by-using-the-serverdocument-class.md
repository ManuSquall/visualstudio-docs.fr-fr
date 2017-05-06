---
title: "Gestion de documents sur un serveur &#224; l&#39;aide de la classe ServerDocument"
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
  - "documents (développement Office dans Visual Studio), gérer sur un serveur"
  - "documents Office (développement Office dans Visual Studio), gérer sur un serveur"
  - "ServerDocument (classe), gérer des documents sur un serveur"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Gestion de documents sur un serveur &#224; l&#39;aide de la classe ServerDocument
  Vous pouvez utiliser la classe ServerDocument dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour gérer plusieurs aspects des personnalisations au niveau du document, même si Microsoft Office Word et Microsoft Office Excel ne sont pas installés.  Vous pouvez effectuer les tâches suivantes :  
  
-   Accéder aux données situées dans le cache de données d'un document ou d'un classeur et modifier ces données.  Pour plus d'informations, consultez [Utilisation des données en mémoire cache dans le document](#CachedData).  
  
-   Gérer l'assembly de personnalisation associé à un document.  Pour plus d'informations, consultez [Gestion de la personnalisation de document](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Présentation de la classe ServerDocument  
 La classe ServerDocument est conçue pour être utilisée sur des ordinateurs sur lesquels Office n'est pas installé.  Par conséquent, vous devez utiliser cette classe dans les applications qui ne s'intègrent pas à Office, telles que les projets de console ou les projets Windows Forms.  Utilisez la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> dans l'assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 La classe ServerDocument peut être utilisée pour traiter les personnalisations au niveau du document créées à l'aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Pour plus d'informations sur Visual Studio 2010 Tools pour Office Runtime et les extensions Office pour .NET Framework, consultez [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si vous possédez une application héritée qui utilise la classe ServerDocument dans le système de Visual Studio Tools pour Office \(version 3,0 Runtime\), le système Visual Studio Tools pour Office \(version 3,0 Runtime\) doit être installé sur les ordinateurs qui exécutent l'application.  Visual Studio 2010 Tools pour Office Runtime ne peut pas exécuter ces applications.  
  
##  <a name="CachedData"></a> Utilisation des données en mémoire cache dans le document  
 La classe ServerDocument fournit des membres que vous pouvez utiliser pour utiliser le cache de données dans des documents personnalisés.  Pour plus d'informations sur les données en mémoire cache, consultez [Mise en cache des données](../vsto/caching-data.md) et [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Le tableau ci\-dessous répertorie les membres que vous pouvez utiliser pour manipuler les données en mémoire cache.  
  
|Tâche|Membre à utiliser|  
|-----------|-----------------------|  
|Pour déterminer si un document contient un cache de données.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Accéder aux données en mémoire cache dans un document.<br /><br /> Pour plus d'informations, consultez [Accès aux données des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|Propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Gestion de la personnalisation de document  
 Vous pouvez utiliser des membres de la classe ServerDocument pour gérer l'assembly de personnalisation associé à un document.  Par exemple, vous pouvez supprimer par programmation la personnalisation d'un document afin que celui\-ci ne fasse plus partie d'une personnalisation.  
  
 Le tableau ci\-dessous répertorie les membres que vous pouvez utiliser pour gérer l'assembly de personnalisation.  
  
|Tâche|Membre à utiliser|  
|-----------|-----------------------|  
|Pour déterminer si un document fait partie d'une personnalisation au niveau du document.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Attacher par programmation une personnalisation à un document au moment de l'exécution.<br /><br /> Pour plus d’informations, consultez [Comment : attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|L'une des méthodes <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.|  
|Supprimer par programmation une personnalisation d'un document au moment de l'exécution.<br /><br /> Pour plus d'informations, consultez [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Obtenir l'URL du manifeste de déploiement associé au document.|Propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## Voir aussi  
 [Comment : attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Vue d'ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Mise en cache des données](../vsto/caching-data.md)  
  
  