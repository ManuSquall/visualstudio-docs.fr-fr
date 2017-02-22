---
title: "Automatisation de la Configuration et les objets SelectedItem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automation (Visual Studio SDK), SelectedItem, objet"
  - "Automation (Visual Studio SDK), génère"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Automatisation de la Configuration et les objets SelectedItem
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez automatiser les processus de génération et d'élément sélectionné dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Automation pour les générations  
 La génération ou la configuration d'un modèle Automation qui est fourni lorsque vous implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>.  Pour plus d'informations, consultez [Présentation des configurations de build](../../ide/understanding-build-configurations.md).  
  
 Si vous créez un VSPackage et souhaitez contrôler les options de configuration, vous devez utiliser le modèle Automation.  
  
## automation pour SelectedItem  
 Vous ne devez pas fournir une implémentation de l'objet d' `SelectedItem` car Visual Studio contient une implémentation standard.  Toutefois, vous pouvez implémenter l'objet d' `SelectedItem` si vous préférez.  Vous devez implémenter un objet contenant l'interface d' `SelectedItem` et retourne une réponse à un appel à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> avec VSITEMID défini à <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Qui contribuent au modèle Automation](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Présentation des configurations de build](../../ide/understanding-build-configurations.md)