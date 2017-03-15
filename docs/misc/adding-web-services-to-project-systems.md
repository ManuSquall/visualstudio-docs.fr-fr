---
title: "Ajout de services web &#224; des syst&#232;mes de projet | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "systèmes de projet, ajout de services web"
  - "services web, ajout aux systèmes de projet VSPackage"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Ajout de services web &#224; des syst&#232;mes de projet
Les services Web XML sont en général, les ressources URL\-adressables qui retournent des informations de programmation au système de projet à l'aide de le protocole SOAP \(protocole SOAP\).  Vous pouvez intégrer des services Web à votre système de projet d'un VSPackage à l'aide de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> .  
  
### pour ajouter un service Web à votre système de projet  
  
1.  Appel `QueryService` pour l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> via le service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> .  
  
2.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>.  Si vous passez au paramètre d' `pDiscoverySession` comme `NULL`, une session de découverte est créée pour vous, et la session est mise en cache afin qu'il soit disponible pour l'usage suivant par l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> .  la méthode d'<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> retourne un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>.  Passez dans l'objet Automation pour le dossier références de service Web comme paramètre d' `pUnkWebReferenceFolder` .  L'environnement Visual Studio vérifie ensuite que le service Web est déjà installé.  Si le service Web n'est pas présent, l'environnement télécharge et ajoute le service Web dans un dossier et à tous les fichiers supplémentaires \(tels que les fichiers .wsdl\) aux nœuds enfants du dossier.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>