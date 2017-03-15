---
title: "Comment&#160;: obtenir un service &#224; partir de l’objet DTE | Microsoft Docs"
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
  - "services, à partir de l’objet DTE"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Comment&#160;: obtenir un service &#224; partir de l’objet DTE
Un service peut être obtenu à partir de n'importe quel programme qui a accès à l'objet d' <xref:EnvDTE.DTEClass> automation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Par exemple, vous pouvez accéder au service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> d'un Assistant via l'objet DTE.  Vous pouvez utiliser ce service pour écrire dans le journal d'activité.  Pour plus d'informations, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
 L'objet DTE implémente <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que vous pouvez utiliser pour rechercher un service de code managé à l'aide de <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
### Pour obtenir un service de l'objet DTE  
  
1.  Le code suivant crée <xref:Microsoft.VisualStudio.Shell.ServiceProvider> de l'objet DTE et appelle <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> avec le type du service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> .  Le service est casté à l'interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>, qui est utilisée pour écrire une entrée dans les journaux d'activité.  Pour plus d'abou d'informations comment écrire dans le journal de l'activité, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## Voir aussi  
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)