---
title: Gérer des documents sur un serveur à l’aide de la classe ServerDocument
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97eed0e4cec143e51195347bfb90d430d8e1eadb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572996"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gérer des documents sur un serveur à l’aide de la classe ServerDocument
  Vous pouvez utiliser la `ServerDocument` classe dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour gérer plusieurs aspects des personnalisations au niveau du document, même si Microsoft Office Word et Microsoft Office Excel ne sont pas installés. Vous pouvez effectuer les tâches suivantes :  
  
-   Accéder et modifier des données dans le cache de données d’un document ou le classeur. Pour plus d’informations, consultez [travailler avec des données mises en cache dans le document](#CachedData).  
  
-   Gérer l’assembly de personnalisation qui est associé à un document. Pour plus d’informations, consultez [gérer la personnalisation de document](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Comprendre la classe ServerDocument  
 La `ServerDocument` classe a été conçue pour être utilisée sur les ordinateurs qui n’ont pas d’Office est installé. Par conséquent, vous utiliserez cette classe dans les applications qui ne s’intègrent pas avec Office, telles que les projets Console ou les projets Windows Forms, plutôt que les projets Office. Utilisez le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe dans le *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* assembly.  
  
 Le `ServerDocument` classe peut être utilisée pour fonctionner sur les personnalisations au niveau du document qui ont été créées à l’aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Pour plus d’informations sur Visual Studio 2010 Tools pour Office Runtime et les extensions Office pour le .NET Framework, consultez [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si vous avez une application héritée qui utilise le `ServerDocument` classe dans le `Visual Studio Tools for Office` system (version 3.0 Runtime), le `Visual Studio Tools for Office` system (version 3.0 runtime) doit être installé sur les ordinateurs qui exécutent l’application. Le `Visual Studio 2010 Tools for Office runtime` ne peut pas exécuter ces applications.  
  
##  <a name="CachedData"></a> Travailler avec des données mises en cache dans le document  
 La `ServerDocument` classe fournit des membres que vous pouvez utiliser pour travailler avec le cache de données dans des documents personnalisés. Pour plus d’informations sur les données mises en cache, consultez [mettre en Cache des données](../vsto/caching-data.md) et [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Le tableau suivant répertorie les membres que vous pouvez utiliser pour travailler avec les données mises en cache.  
  
|Tâche|Membre à utiliser|  
|----------|-------------------|  
|Pour déterminer si un document a un cache de données.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>|  
|Pour accéder aux données mises en cache dans un document.<br /><br /> Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Gérer la personnalisation de document  
 Vous pouvez utiliser des membres de la `ServerDocument` classe pour gérer l’assembly de personnalisation qui est associé à un document. Par exemple, vous pouvez supprimer par programmation la personnalisation d’un document afin que le document ne fait plus partie d’une personnalisation.  
  
 Le tableau suivant répertorie les membres que vous pouvez utiliser pour gérer l’assembly de personnalisation.  
  
|Tâche|Membre à utiliser|  
|----------|-------------------|  
|Pour déterminer si un document fait partie d’une personnalisation au niveau du document.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>|  
|Pour joindre par programmation une personnalisation à un document au moment de l’exécution.<br /><br /> Pour plus d’informations, consultez [Comment : attacher à des documents, les extensions de code managé](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Parmi les <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthodes.|  
|Pour supprimer par programme une personnalisation à partir d’un document au moment de l’exécution.<br /><br /> Pour plus d’informations, consultez [Comment : supprimer gérés des Extensions de code à partir de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>|  
|Pour obtenir l’URL du manifeste de déploiement qui est associé au document.|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : attacher à des documents, les extensions de code managé](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Comment : supprimer des extensions de code managé à partir de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Données du cache](../vsto/caching-data.md)  
  