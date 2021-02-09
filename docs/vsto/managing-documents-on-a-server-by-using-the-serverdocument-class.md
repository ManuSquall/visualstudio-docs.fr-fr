---
title: Gérer des documents sur un serveur à l’aide de la classe ServerDocument
description: Découvrez comment vous pouvez utiliser la classe ServerDocument dans le Visual Studio Tools pour Office Runtime pour gérer plusieurs aspects des personnalisations au niveau du document.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17a25ca382cfbbc762731afacaa628de616cfe1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879473"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gérer des documents sur un serveur à l’aide de la classe ServerDocument
  Vous pouvez utiliser la `ServerDocument` classe dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour gérer plusieurs aspects des personnalisations au niveau du document, même si Microsoft Office Word et Microsoft Office Excel ne sont pas installés. Vous pouvez effectuer les tâches suivantes :

- Accéder aux données dans le cache de données d’un document ou d’un classeur et les modifier. Pour plus d’informations, consultez [utiliser des données mises en cache dans le document](#CachedData).

- Gérer l’assembly de personnalisation associé à un document. Pour plus d’informations, consultez [gérer la personnalisation de document](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Comprendre la classe ServerDocument
 La `ServerDocument` classe est conçue pour être utilisée sur des ordinateurs sur lesquels Office n’est pas installé. Par conséquent, vous utilisez généralement cette classe dans des applications qui ne s’intègrent pas à Office, telles que les projets de console ou les projets de Windows Forms, plutôt que les projets Office. Utilisez la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe dans l’assembly *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

 La `ServerDocument` classe peut être utilisée pour opérer sur les personnalisations au niveau du document créées à l’aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Pour plus d’informations sur Visual Studio 2010 Tools pour Office Runtime et les extensions Office pour le .NET Framework, consultez [Visual Studio Tools pour Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Si vous disposez d’une application héritée qui utilise la `ServerDocument` classe dans le `Visual Studio Tools for Office` système (version 3,0 Runtime), le `Visual Studio Tools for Office` système (Runtime version 3,0) doit être installé sur les ordinateurs qui exécutent l’application. Le `Visual Studio 2010 Tools for Office runtime` ne peut pas exécuter ces applications.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Utiliser des données mises en cache dans le document
 La `ServerDocument` classe fournit des membres que vous pouvez utiliser pour travailler avec le cache de données dans des documents personnalisés. Pour plus d’informations sur les données mises en cache, consultez mettre [en cache](../vsto/caching-data.md) les données et [accéder aux données dans les documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).

 Le tableau suivant répertorie les membres que vous pouvez utiliser pour travailler avec des données mises en cache.

|Tâche|Membre à utiliser|
|----------|-------------------|
|Pour déterminer si un document a un cache de données.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>|
|Pour accéder aux données mises en cache dans un document.<br /><br /> Pour plus d’informations, consultez [accéder aux données dans les documents sur le serveur](../vsto/accessing-data-in-documents-on-the-server.md).|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Gérer la personnalisation des documents
 Vous pouvez utiliser les membres de la `ServerDocument` classe pour gérer l’assembly de personnalisation associé à un document. Par exemple, vous pouvez supprimer par programmation la personnalisation d’un document afin que le document ne fasse plus partie d’une personnalisation.

 Le tableau suivant répertorie les membres que vous pouvez utiliser pour gérer l’assembly de personnalisation.

|Tâche|Membre à utiliser|
|----------|-------------------|
|Pour déterminer si un document fait partie d’une personnalisation au niveau du document.|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>|
|Pour attacher par programmation une personnalisation à un document au moment de l’exécution.<br /><br /> Pour plus d’informations, consultez [Comment : attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Une des <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> méthodes.|
|Pour supprimer par programmation une personnalisation d’un document au moment de l’exécution.<br /><br /> Pour plus d’informations, consultez [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Méthode <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>|
|Pour récupérer l’URL du manifeste de déploiement associé au document.|La propriété <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|

## <a name="see-also"></a>Voir aussi
- [Comment : attacher des extensions de code managé à des documents](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Comment : supprimer des extensions de code managé de documents](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Données de cache](../vsto/caching-data.md)
