---
title: 'Comment : utiliser GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948180"
---
# <a name="how-to-use-getglobalservice"></a>Procédure : utilisation d’un GetGlobalService
Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou d’un conteneur de contrôle qui n’a pas été sur site, ou avec un fournisseur de services qui ne connaît pas le service souhaité. Par exemple, vous souhaiterez peut-être écrire dans le journal d’activité à partir d’un contrôle. Pour plus d’informations sur ces scénarios et d’autres, consultez Guide pratique [pour résoudre les problèmes liés aux services](../extensibility/how-to-troubleshoot-services.md).  
  
 Vous pouvez accéder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à la plupart des services en appelant la <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode statique.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> s’appuie sur un fournisseur de services mis en cache qui est initialisé la première fois qu’un VSPackage dérivé de <xref:Microsoft.VisualStudio.Shell.Package> est sur site. Vous devez vous assurer que cette condition est remplie ou être préparée pour un service null.  
  
 Heureusement, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> fonctionne bien la plupart du temps.  
  
- Si un VSPackage fournit un service connu uniquement d’un autre VSPackage, le VSPackage qui demande le service est sur site avant le chargement du VSPackage.  
  
- Si une fenêtre outil est créée par un VSPackage, le VSPackage est sur site avant la création de la fenêtre outil.  
  
- Si un conteneur de contrôle est hébergé par une fenêtre outil créée par un VSPackage, le VSPackage est sur site avant que le conteneur de contrôle ne soit créé.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Pour obtenir un service à partir d’une fenêtre outil ou d’un conteneur de contrôle  
  
- Insérez ce code dans le constructeur, la fenêtre outil ou le conteneur de contrôle :  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Ce code obtient un service SVsActivityLog et le convertit en <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, qui peut être utilisée pour écrire dans le journal d’activité. Pour obtenir un exemple, consultez [procédure : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : dépanner des services](../extensibility/how-to-troubleshoot-services.md)   
 [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)