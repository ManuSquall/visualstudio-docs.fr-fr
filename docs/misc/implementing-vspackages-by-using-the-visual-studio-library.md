---
title: "Impl&#233;mentation de VSPackages &#224; l’aide de la biblioth&#232;que Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bibliothèque Visual Studio, implémentation VSPackages"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# Impl&#233;mentation de VSPackages &#224; l’aide de la biblioth&#232;que Visual Studio
La classe d' `IVsPackageImpl` dans la bibliothèque Visual Studio fournit une implémentation minimale de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .  `IVsPackageImpl` se charge de la plupart des méthodes de maintenance d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  D'autres méthodes que vous pouvez avoir besoin de substituer pour fournir une implémentation explicite incluent :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  Le modèle de package de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère l'erreur tout le code présenté ici.  Vous pouvez gagner du temps à l'aide de le modèle de générer un VSPackage pour vous.  
  
 Les packages qui sont implémentés à l'aide de la bibliothèque de Visual Studio en général héritent d'une classe d'un VSPackage de [CComObjectRootEx Class](/visual-cpp/atl/reference/ccomobjectrootex-class) ATL et de [CComCoClass Class](/visual-cpp/atl/reference/ccomcoclass-class) et d'IVsPackageImpl de la bibliothèque de Visual Studio.  Par exemple, le traçage est la déclaration de classe d'un VSPackage de l'exemple de Reference.Package :  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 Les paramètres du modèle d' `IVsPackageImpl` affichés sont la classe d'un VSPackage elle\-même et un pointeur vers un GUID identifiant le VSPackage.  
  
## Prendre en charge QueryInterface avec les mappages COM  
 Pour obtenir la prise en charge ATL d' `QueryInterface`, son mappage COM doit répertorier les interfaces que la classe implémente.  Par exemple, le traçage est le mappage COM pour la classe d'un VSPackage dans l'exemple de Reference.Package :  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 Pour plus d'informations sur les mappages COM, consultez [Implementing CComObjectRootEx](/visual-cpp/atl/implementing-ccomobjectrootex) et le [COM\_INTERFACE\_ENTRY Macros](../Topic/COM_INTERFACE_ENTRY%20Macros.md).  
  
## Inscription de prise en charge avec le mappage de Registre  
 La bibliothèque de Visual Studio utilise les fichiers de style ATL de .RGS pour prendre en charge l'alignement des objets COM.  Pour prendre en charge le remplacement de jeton dans le fichier de .RGS, la bibliothèque Visual Studio utilise des mappages de Registre.  Les mappages de Registre répertorient les symboles à remplacer et prennent en charge l'utilisation des identificateurs pour les ressources de table de chaînes.  
  
 Par exemple, le traçage est le mappage de Registre de la classe d'un VSPackage dans l'exemple de Reference.Package :  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## Voir aussi  
 [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md)