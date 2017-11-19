---
title: "Gestion de Documents sur un serveur à l’aide de la classe ServerDocument | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd24d18df965535ee1315ae7807ac23723dc51d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Gestion de documents sur un serveur à l'aide de la classe ServerDocument
  Vous pouvez utiliser la classe ServerDocument dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour gérer plusieurs aspects des personnalisations au niveau du document, même si Microsoft Office Word et Microsoft Office Excel ne sont pas installés. Vous pouvez effectuer les tâches suivantes :  
  
-   Accéder et modifier des données dans le cache de données d’un document ou le classeur. Pour plus d’informations, consultez [utilisation des données mises en cache dans le Document](#CachedData).  
  
-   Gérer l’assembly de personnalisation qui est associé à un document. Pour plus d’informations, consultez [gestion de la personnalisation de Document](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Présentation de la classe ServerDocument  
 La classe ServerDocument est conçue pour être utilisé sur les ordinateurs qui n’ont pas d’Office est installé. Par conséquent, vous utiliserez cette classe dans les applications qui ne s’intègrent pas avec Office, telles que les projets Console ou les projets Windows Forms, plutôt que les projets Office. Utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe dans l’assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 La classe ServerDocument peut être utilisée pour fonctionner sur les personnalisations au niveau du document qui ont été créées à l’aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Pour plus d’informations sur Visual Studio 2010 Tools pour Office Runtime et les extensions Office pour le .NET Framework, consultez [Visual Studio Tools pour Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si vous avez une application héritée qui utilise la classe ServerDocument dans Visual Studio Tools pour Office system (version 3.0 Runtime), Visual Studio Tools pour Office system (version 3.0 Runtime) doit être installé sur les ordinateurs qui exécutent l’application. Visual Studio 2010 Tools pour Office Runtime ne peut pas exécuter ces applications.  
  
##  <a name="CachedData"></a>Utilisation des données mises en cache dans le Document  
 La classe ServerDocument fournit des membres que vous pouvez utiliser pour travailler avec le cache de données dans des documents personnalisés. Pour plus d’informations sur les données mises en cache, consultez [mise en cache des données](../vsto/caching-data.md) et [accès aux données des Documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Le tableau suivant répertorie les membres que vous pouvez utiliser pour travailler avec les données mises en cache.  
  
|Tâche|Membre à utiliser|  
|----------|-------------------|  
|Pour déterminer si un document a un cache de données.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>|  
|Pour accéder aux données mises en cache dans un document.<br /><br /> Pour plus d'informations, consultez [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a>Gestion de la personnalisation de Document  
 Vous pouvez utiliser des membres de la classe ServerDocument pour gérer l’assembly de personnalisation qui est associé à un document. Par exemple, vous pouvez supprimer par programmation la personnalisation d’un document afin que le document ne fait plus partie d’une personnalisation.  
  
 Le tableau suivant répertorie les membres que vous pouvez utiliser pour gérer l’assembly de personnalisation.  
  
|Tâche|Membre à utiliser|  
|----------|-------------------|  
|Pour déterminer si un document fait partie d’une personnalisation au niveau du document.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>|  
|Pour joindre par programmation une personnalisation à un document au moment de l’exécution.<br /><br /> Pour plus d’informations, consultez [Comment : joindre des Extensions de Code managé à des Documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Parmi les <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthodes.|  
|Pour supprimer par programme une personnalisation à partir d’un document au moment de l’exécution.<br /><br /> Pour plus d’informations, consultez [Comment : supprimer des Extensions de Code managé à partir de Documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>|  
|Pour obtenir l’URL du manifeste de déploiement qui est associé au document.|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : attacher des Extensions de Code managé à des Documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Comment : supprimer des Extensions de Code managé de Documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Mise en cache des données](../vsto/caching-data.md)  
  