---
title: "FAQ concernant l’installation et le d&#233;ploiement | Microsoft Docs"
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
  - "déploiement [Visual Studio SDK]"
  - "LCID [Visual Studio SDK]"
  - "installation [Visual Studio SDK]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# FAQ concernant l’installation et le d&#233;ploiement
Cette rubrique explique comment résoudre les erreurs de communauté d'utilisateurs de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sur l'installation et de déploiement.  La rubrique continue à être mis à jour avec le nouveau contenu de la communauté.  
  
## Sommaire  
  
-   [Détermination LCID d'une installation de Visual Studio par programme](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> Détermination LCID d'une installation de Visual Studio par programme  
 **q :** Existe \-t\-il un moyen par programme déterminent\-il LCID d'une installation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ?  
  
 **Un :**  <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>retournera LCID de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en cours de utilisation.  
  
## Voir aussi  
 [Publication d’un produit](../misc/releasing-a-visual-studio-integration-product.md)