---
title: Enregistrement des générateurs de fichiers uniques (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705809"
---
# <a name="registering-single-file-generators"></a>Inscription de générateurs de fichier unique
Pour rendre un outil [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]personnalisé disponible en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous devez l’enregistrer afin de pouvoir l’instantanér et l’associer à un type de projet particulier.

### <a name="to-register-a-custom-tool"></a>Pour enregistrer un outil personnalisé

1. Enregistrez l’outil personnalisé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL soit dans le registre local ou dans le registre du système, sous HKEY_CLASSES_ROOT.

    Par exemple, voici les informations d’inscription pour l’outil personnalisé MSDataSetGenerator géré, qui vient avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Créez une clé de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registre dans\\la ruche désirée sous Generators*GUID* où *le GUID* est le GUID défini par le système ou le service de projet de la langue spécifique. Le nom de la clé devient le nom programmatique de votre outil personnalisé. La clé d’outil personnalisée a les valeurs suivantes :

   - (Par défaut)

        facultatif. Fournit une description conviviale de l’outil personnalisé. Ce paramètre est facultatif, mais recommandé.

   - CLSID

        Obligatoire. Précise l’identifiant de la bibliothèque de classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>du composant COM qui met en œuvre .

   - GeneratesDesignTimeSource

        Obligatoire. Indique si les types de fichiers produits par cet outil personnalisé sont mis à la disposition des concepteurs visuels. La valeur de ce paramètre doit être (zéro) 0 pour les types non disponibles pour les concepteurs visuels ou (un) 1 pour les types disponibles pour les concepteurs visuels.

   > [!NOTE]
   > Vous devez enregistrer l’outil personnalisé séparément pour chaque langue pour laquelle vous souhaitez que l’outil personnalisé soit disponible.

    Par exemple, le MSDataSetGenerator s’inscrit une fois pour chaque langue :

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
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)
- [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Introduction à l'objet BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
