---
title: "Proc&#233;dure&#160;: inscription d’un service | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, inscription"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Proc&#233;dure&#160;: inscription d’un service
Un MPF \(Managed Package Framework\) fournit des attributs permettant de contrôler l’inscription des services gérés. L’utilitaire RegPkg utilise ces attributs pour inscrire un service dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Exemple  
 Le code qui suit est issu des [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> inscrit le service SMyGlobalService dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations sur <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> et <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, voir [Inscription et annulation de l’enregistrement de packages VS](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Pour inscrire un service devant remplacer un autre service portant le même nom, utilisez <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> au lieu de <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## Programmation fiable  
 Pour faciliter la recompilation d’un fournisseur de services sans modifier le client du service, ou inversement, vous pouvez définir le service et ses interfaces dans un module d’assembly distinct. Le code suivant provient du fichier IMyGlobalService.cs de l’exemple Reference.Services \(C\#\).  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> est nécessaire pour obtenir l’interface à partir de code non managé.  
  
> [!NOTE]
>  Même s’il est possible d’utiliser le même type ou le même GUID pour le service et l’interface, nous vous le déconseillons, car un service peut exposer plusieurs interfaces.  
  
## Voir aussi  
 [Registering VSPackages](http://msdn.microsoft.com/fr-fr/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Service Essentials](../extensibility/internals/service-essentials.md)