---
title: "Proc&#233;dure&#160;: personnalisation d’un VSPackage (C++) | Microsoft Docs"
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
  - "Boîte de dialogue À propos de"
  - "VSPackages, écrans de démarrage"
  - "VSPackages, personnalisation"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Proc&#233;dure&#160;: personnalisation d’un VSPackage (C++)
Pour afficher dans la boîte de dialogue de **À propos de** et l'écran de démarrage, VSPackages doit implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> .  Cela fournit les informations suivantes dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Nom  
  
-   ID, tel que l'interface série ou le numéro de version  
  
-   Information  
  
-   icône de logo  
  
 La classe d' `IVsInstalledProductImpl` accepte des paramètres de modèle pour ces informations.  Chaque paramètre de modèle est un ID  les trois premiers sont des identificateurs des ressources de type chaîne et le quatrième est l'ID de ressource d'une icône.  
  
## Exemple  
 La déclaration de classe suivante de la classe d'un VSPackage est de [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 Pour tester votre VSPackage, consultez [Comment : tester la boîte de dialogue À propos de du menu Aide et l’écran de démarrage](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Voir aussi  
 [Personnalisation de VSPackage](/visual-cpp/misc/vspackage-branding)