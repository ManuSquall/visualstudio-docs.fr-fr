---
title: "Enregistrement de générateurs de fichier unique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 239f68b8bdbaf910f25b9fbe6e0fdd7061fe0f16
ms.lasthandoff: 02/22/2017

---
# <a name="registering-single-file-generators"></a>Enregistrement de générateurs de fichier unique
Pour mettre à disposition dans un outil personnalisé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez donc l’enregistrer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut instancier et l’associe à un type de projet particulier.  
  
### <a name="to-register-a-custom-tool"></a>Pour enregistrer un outil personnalisé  
  
1.  Inscription de l’outil personnalisé DLL soit dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] du Registre local ou dans le Registre système, sous HKEY_CLASSES_ROOT.  
  
     Par exemple, voici les informations d’inscription pour l’outil personnalisé MSDataSetGenerator géré qui est fourni avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Créer une clé de Registre dans l’élément [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive sous générateurs\\*GUID* où *GUID* est le GUID défini par de la langue système de projet ou un service. Le nom de la clé devient le nom de programmation de votre outil personnalisé. La clé de l’outil personnalisé a les valeurs suivantes :  
  
    -   (Default)  
  
         Facultatif. Fournit une description conviviale de l’outil personnalisé. Ce paramètre est facultatif, mais recommandé.  
  
    -   CLSID  
  
         Obligatoire. Spécifie l’identificateur de la bibliothèque de classes du composant COM qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
  
    -   GeneratesDesignTimeSource  
  
         Obligatoire. Indique si les types de fichiers générés par cet outil personnalisé sont disponibles pour les concepteurs visuels. La valeur de ce paramètre doit être (zéro) 0 pour les types non disponibles pour les concepteurs visuels ou 1 (un) pour les types disponibles pour les concepteurs visuels.  
  
    > [!NOTE]
    >  Vous devez enregistrer l’outil personnalisé séparément pour chaque langage pour lequel vous souhaitez l’outil personnalisé soit disponible.  
  
     Par exemple, le MSDataSetGenerator inscrit qu’une seule fois pour chaque langue :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [L’implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)   
 [Déterminer le Namespace par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposer des Types pour les concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introduction à l’objet BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
