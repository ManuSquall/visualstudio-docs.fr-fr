---
title: "Proc&#233;dure&#160;: utilisation d’un GetGlobalService | Microsoft Docs"
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
  - "Services, GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Proc&#233;dure&#160;: utilisation d’un GetGlobalService
Quelquefois vous devrez peut\-être obtenir un service à partir d'une fenêtre Outil ou d'un conteneur de contrôle qui n'ont pas été installés, ou bien a été installé avec un fournisseur de services qui ne sait pas celui que vous souhaitez.  Par exemple, vous pouvez écrire dans le journal d'activité d'un contrôle.  Pour plus d'informations sur ces éléments et d'autres scénarios, consultez [Comment : résoudre les problèmes des Services](../extensibility/how-to-troubleshoot-services.md).  
  
 vous pouvez obtenir la plupart des services de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en appelant la méthode statique d' <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> repose sur un fournisseur de services en cache qui est initialisé la première fois tout VSPackage dérivé d' <xref:Microsoft.VisualStudio.Shell.Package> se trouve.  Vous devez vous assurer que cette condition est remplie, ou bien être préparé pour un service null.  
  
 heureusement, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> fonctionne correctement le plus souvent.  
  
-   Si un VSPackage fournit un service connu uniquement à un autre VSPackage, le VSPackage qui demande le service se trouve avant que le VSPackage fournissant le service chargé.  
  
-   Si une fenêtre Outil est créée par un VSPackage, le VSPackage se trouve avant que la fenêtre Outil soit créée.  
  
-   Si un conteneur de contrôle est hébergé par une fenêtre Outil créée par un VSPackage, le VSPackage se trouve avant que le conteneur de contrôle créé.  
  
### Pour obtenir un service à partir d'une fenêtre Outil ou d'un conteneur de contrôle  
  
-   insérez ce code dans le constructeur, la fenêtre Outil, ou le conteneur de contrôle :  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     Ce code obtient un service et les casts de SVsActivityLog il à une interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> , qui peut être utilisée pour écrire dans le journal d'activité.  Pour obtenir un exemple, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
## Voir aussi  
 [Comment : résoudre les problèmes des Services](../extensibility/how-to-troubleshoot-services.md)   
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)