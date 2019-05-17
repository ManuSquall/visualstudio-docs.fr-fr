---
title: 'Procédure : Inscrire un Service | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408424"
---
# <a name="how-to-register-a-service"></a>Procédure : Inscrire un Service
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
> Même s’il est possible d’utiliser le même type ou le même GUID pour le service et l’interface, nous vous le déconseillons, car un service peut exposer plusieurs interfaces.  
  
## <a name="see-also"></a>Voir aussi  
 [Inscription de VSPackages](../extensibility/internals/registering-vspackages.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)