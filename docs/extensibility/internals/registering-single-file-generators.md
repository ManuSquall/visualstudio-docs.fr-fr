---
title: "L’inscription des générateurs de fichier unique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 22261c7485f1779eb3613c7ef5af693feeb51fbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="registering-single-file-generators"></a>L’inscription des générateurs de fichier unique
Pour utiliser un outil personnalisé dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez l’inscrire donc [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut instancier et l’associe à un type de projet particulier.  
  
### <a name="to-register-a-custom-tool"></a>Pour inscrire un outil personnalisé  
  
1.  Inscrire l’outil personnalisé DLL soit dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registre local ou dans le Registre système, sous HKEY_CLASSES_ROOT.  
  
     Par exemple, voici les informations d’inscription pour l’outil personnalisé MSDataSetGenerator managé qui est livré avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Créer une clé de Registre dans l’élément [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ruche sous générateurs\\*GUID* où *GUID* est le GUID défini par de la langue système de projet ou un service. Le nom de la clé devient le nom de programmation de votre outil personnalisé. La clé de l’outil personnalisé a les valeurs suivantes :  
  
    -   (Default)  
  
         Facultatif. Fournit une description conviviale de l’outil personnalisé. Ce paramètre est facultatif, mais recommandé.  
  
    -   CLSID  
  
         Obligatoire. Spécifie l’identificateur de la bibliothèque de classes du composant COM qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Obligatoire. Indique si les types à partir des fichiers produits par cet outil personnalisé sont disponibles pour les concepteurs visuels. La valeur de ce paramètre doit être (zéro) 0 pour les types non disponibles pour les concepteurs visuels ou 1 (un) pour les types disponibles pour les concepteurs visuels.  
  
    > [!NOTE]
    >  Vous devez inscrire l’outil personnalisé séparément pour chaque langue pour laquelle vous souhaitez l’outil personnalisé soit disponible.  
  
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
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)   
 [Exposer des Types de concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Présentation de l’objet BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)