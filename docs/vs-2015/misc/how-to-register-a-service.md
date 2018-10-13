---
title: 'Comment : inscrire un Service | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a1f8026a648b2a0809af17664d4399f815c329be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206256"
---
# <a name="how-to-register-a-service"></a>Procédure : inscription d’un service
Un MPF (Managed Package Framework) fournit des attributs permettant de contrôler l’inscription des services gérés. L’utilitaire RegPkg utilise ces attributs pour inscrire un service dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Exemple  
 Le code qui suit est issu [exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> inscrit le service SMyGlobalService dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations sur <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> et <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, consultez [inscription et annulation de l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Pour inscrire un service devant remplacer un autre service portant le même nom, utilisez <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> au lieu de <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Pour faciliter la recompilation d’un fournisseur de services sans modifier le client du service, ou inversement, vous pouvez définir le service et ses interfaces dans un module d’assembly distinct. Le code suivant provient du fichier IMyGlobalService.cs de l’exemple Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> est nécessaire pour obtenir l’interface à partir de code non managé.  
  
> [!NOTE]
>  Même s’il est possible d’utiliser le même type ou le même GUID pour le service et l’interface, nous vous le déconseillons, car un service peut exposer plusieurs interfaces.  
  
## <a name="see-also"></a>Voir aussi  
 [Inscription de VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)