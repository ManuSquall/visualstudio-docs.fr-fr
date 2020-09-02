---
title: Inscription de générateurs de fichiers uniques | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696102"
---
# <a name="registering-single-file-generators"></a>Inscription de générateurs de fichier unique
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour rendre un outil personnalisé disponible dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , vous devez l’inscrire afin qu’il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] puisse l’instancier et l’associe à un type de projet particulier.  
  
### <a name="to-register-a-custom-tool"></a>Pour inscrire un outil personnalisé  
  
1. Inscrivez la DLL de l’outil personnalisé dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Registre local ou dans le registre système, sous HKEY_CLASSES_ROOT.  
  
     Par exemple, Voici les informations d’inscription de l’outil personnalisé MSDataSetGenerator géré, qui est fourni avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Créez une clé de Registre dans la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ruche souhaitée sous GUID des générateurs, \\ *GUID* où *GUID* est le GUID défini par le service ou le système de projet du langage spécifique. Le nom de la clé devient le nom de programmation de votre outil personnalisé. La clé de l’outil personnalisé a les valeurs suivantes :  
  
    - (Par défaut)  
  
         facultatif. Fournit une description conviviale de l’outil personnalisé. Ce paramètre est facultatif, mais recommandé.  
  
    - CLSID  
  
         Obligatoire. Spécifie l’identificateur de la bibliothèque de classes du composant COM qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - GeneratesDesignTimeSource  
  
         Obligatoire. Indique si les types des fichiers produits par cet outil personnalisé sont mis à la disposition des concepteurs visuels. La valeur de ce paramètre doit être (zéro) 0 pour les types qui ne sont pas disponibles pour les concepteurs visuels ou (un) 1 pour les types disponibles pour les concepteurs visuels.  
  
    > [!NOTE]
    > Vous devez inscrire l’outil personnalisé séparément pour chaque langue pour laquelle vous souhaitez que l’outil personnalisé soit disponible.  
  
     Par exemple, le MSDataSetGenerator s’inscrit pour chaque langue :  
  
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
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)   
 [Détermination de l’espace de noms par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposer des types à des concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introduction à l'objet BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
