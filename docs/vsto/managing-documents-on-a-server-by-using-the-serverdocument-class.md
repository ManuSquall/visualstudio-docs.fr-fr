---
title: Gérer des documents sur un serveur à l’aide de la classe ServerDocument
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f776b73b4f80756a36a5ad4610a60440a6f9abd1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876068"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gérer des documents sur un serveur à l’aide de la classe ServerDocument
  Vous pouvez utiliser la `ServerDocument` classe dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour gérer plusieurs aspects de personnalisations au niveau du document, même si Microsoft Office Word et Microsoft Office Excel ne sont pas installés. Vous pouvez effectuer les tâches suivantes :  
  
- Accéder et modifier des données dans le cache de données d’un document ou classeur. Pour plus d’informations, consultez [travailler avec des données mises en cache dans le document](#CachedData).  
  
- Gérer l’assembly de personnalisation associé à un document. Pour plus d’informations, consultez [gérer la personnalisation de document](#CustomizationInfo).  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Identifiez la classe ServerDocument  
 Le `ServerDocument` classe est conçue pour être utilisée sur les ordinateurs qui n’ont pas d’Office sont installées. Par conséquent, vous utilisez généralement cette classe dans les applications qui ne s’intègrent pas avec Office, telles que des projets Console ou les projets Windows Forms, plutôt que les projets Office. Utilisez le <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe dans le *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* assembly.  
  
 Le `ServerDocument` classe peut être utilisée pour opérer sur les personnalisations au niveau du document qui ont été créées à l’aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Pour plus d’informations sur Visual Studio 2010 Tools pour Office Runtime et les extensions Office pour le .NET Framework, consultez [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si vous avez une application héritée qui utilise le `ServerDocument` classe dans le `Visual Studio Tools for Office` system (version 3.0 Runtime), le `Visual Studio Tools for Office` system (version 3.0 runtime) doit être installé sur les ordinateurs qui exécutent l’application. Le `Visual Studio 2010 Tools for Office runtime` ne peut pas exécuter ces applications.  
  
##  <a name="CachedData"></a> Travailler avec des données mises en cache dans le document  
 Le `ServerDocument` classe fournit des membres que vous pouvez utiliser pour travailler avec le cache de données dans des documents personnalisés. Pour plus d’informations sur les données mises en cache, consultez [mettre en Cache données](../vsto/caching-data.md) et [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Le tableau suivant répertorie les membres que vous pouvez utiliser pour travailler avec les données mises en cache.  
  
|Tâche|Membre à utiliser|  
|----------|-------------------|  
|Pour déterminer si un document a un cache de données.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>|  
|Accéder aux données mises en cache dans un document.<br /><br /> Pour plus d’informations, consultez [accéder aux données dans des documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Gérer la personnalisation de document  
 Vous pouvez utiliser les membres de la `ServerDocument` classe pour gérer l’assembly de personnalisation associé à un document. Par exemple, vous pouvez supprimer par programmation la personnalisation d’un document afin que le document ne fait plus partie d’une personnalisation.  
  
 Le tableau suivant répertorie les membres que vous pouvez utiliser pour gérer l’assembly de personnalisation.  
  
|Tâche|Membre à utiliser|  
|----------|-------------------|  
|Pour déterminer si un document fait partie d’une personnalisation au niveau du document.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>|  
|Pour joindre par programmation une personnalisation à un document lors de l’exécution.<br /><br /> Pour plus d'informations, voir [Procédure : Attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Parmi les <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthodes.|  
|Pour supprimer par programme une personnalisation à partir d’un document en cours d’exécution.<br /><br /> Pour plus d'informations, voir [Procédure : Supprimer des Extensions de code managé à partir de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>|  
|Pour obtenir l’URL du manifeste de déploiement qui est associé au document.|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Guide pratique pour Supprimer des extensions de code managé à partir de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Données du cache](../vsto/caching-data.md)  
