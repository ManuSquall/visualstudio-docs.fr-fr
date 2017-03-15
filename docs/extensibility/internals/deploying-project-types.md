---
title: "Types de projets de d&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), le code managé"
  - "agrégation (Visual Studio SDK), de projets"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Types de projets de d&#233;ploiement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installe une nouvelle agrégation de type de projet \(ProjectAggregator2.dll\) et également un package Windows Installer pour la redistribution \(ProjectAggregator2.msi\). Vous devez utiliser la nouvelle fonction d'agrégation pour les types de projets de code managé. ProjectAggregator2 fonctionne limitations de solutions dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet agrégateur qui empêchent les types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser la nouvelle fonction d'agrégation.  
  
1.  Supprimer le projet NativeHierarchyWrapper de votre solution.  
  
2.  Supprimez les fichiers binaires NativeHierarchyWrapper de votre installation.  
  
3.  Ajoutez ProjectAggregator2.msi à votre configuration.