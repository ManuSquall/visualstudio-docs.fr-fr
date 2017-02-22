---
title: "Prise en charge d&#39;Automation pour les Pages d&#39;Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pages d'Options Outils (Visual Studio SDK), prise en charge automation"
  - "Automation (Visual Studio SDK), créer des pages d'Options Outils"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Prise en charge d&#39;Automation pour les Pages d&#39;Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Packages VS peuvent fournir personnalisée **Options** boîtes de dialogue pour le **outils** menu \(pages d'Options Outils\) dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et peut les rendre disponibles pour le modèle automation.  
  
## Pages d'Options Outils  
 Pour créer un **Outils\/Options** page, un VSPackage doit fournir une implémentation de contrôle utilisateur retournée à l'environnement de mise en œuvre du VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> \(méthode\), \(ou pour le code managé le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode\).  
  
 Il est facultatif, mais il est vivement recommandé d'autoriser l'accès à cette nouvelle page via le modèle automation. Pour cela, les étapes suivantes :  
  
1.  Étendre le <xref:EnvDTE._DTE.Properties%2A> objet via l'implémentation d'un objet dérivé de IDispatch.  
  
2.  Retourner une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> \(méthode\) \(ou pour le code managé du <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> \(méthode\)\) à l'objet dérivé de IDispatch.  
  
3.  Lorsqu'un client automation appelle la <xref:EnvDTE._DTE.Properties%2A> méthode personnalisé **Option** page de propriétés, l'environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode pour obtenir un personnalisé **Outils\/Options** implémentation d'automation de la page.  
  
4.  L'objet automation du VSPackage sert ensuite à fournir chacun <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A>.  
  
 Pour obtenir un exemple d'implémentation d'une page Outils\/Options personnalisée, consultez [Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md).  
  
## Voir aussi  
 [Exposer des objets de projet](../../extensibility/internals/exposing-project-objects.md)