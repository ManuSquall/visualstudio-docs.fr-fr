---
title: 'Procédure : Utilisation d’un GetGlobalService | Microsoft Docs'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62948180"
---
# <a name="how-to-use-getglobalservice"></a>Procédure : Utilisation d’un GetGlobalService
Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou le contrôle conteneur qui n’a pas été installé, ou bien a été installé avec un fournisseur de services qui ne sait pas sur le service que vous souhaitez. Par exemple, vous souhaiterez peut-être écrire dans le journal d’activité à partir d’un contrôle. Pour plus d’informations sur ces scénarios et d’autres, consultez [Comment : Dépanner les Services](../extensibility/how-to-troubleshoot-services.md).  
  
 Vous pouvez obtenir la plupart des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] services en appelant la méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (méthode).  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> s’appuie sur un fournisseur de services de mise en cache qui est initialisé à la première fois qu’un VSPackage dérivé <xref:Microsoft.VisualStudio.Shell.Package> est placé. Vous devez vous assurer que cette condition est remplie, ou bien être préparée pour un service de type null.  
  
 Heureusement, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> fonctionne correctement la plupart du temps.  
  
- Si un VSPackage fournit un service connu uniquement à un autre package Visual Studio, le VSPackage demandant le service est placé avant le VSPackage pour fournir que le service est chargé.  
  
- Si une fenêtre outil est créée par un VSPackage, le VSPackage est placé avant la création de la fenêtre outil.  
  
- Si un conteneur de contrôle est hébergé par une fenêtre outil créée par un VSPackage, le VSPackage est placé avant le conteneur de contrôle est créé.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Pour obtenir un service à partir d’un conteneur de contrôle ou de la fenêtre outil  
  
- Insérez ce code dans le constructeur, une fenêtre outil ou un conteneur de contrôle :  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Ce code obtient un service SVsActivityLog et caste vers une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, ce qui peut être utilisé pour écrire dans le journal d’activité. Pour voir un exemple, consultez [Comment : Utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Résoudre les problèmes des Services](../extensibility/how-to-troubleshoot-services.md)   
 [À l’aide et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)