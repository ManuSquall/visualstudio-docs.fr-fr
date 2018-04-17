---
title: Prise en charge plusieurs Versions de Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 317ec1f214d18989c3b2c5c27fe9df9309239631
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Prise en charge plusieurs Versions de Visual Studio
Le terme *côte-à-côte* signifie que vous pouvez installer et gérer plusieurs versions d’un produit sur le même ordinateur. VSPackages, cela signifie que d’un utilisateur peut avoir plusieurs versions de Visual Studio installées sur le même ordinateur. Toutefois, vous ne peut pas avoir des versions côte à côte de vos VSPackages chargées dans une seule version de Visual Studio.  
  
 Avant d’apporter votre VSPackage peut être chargé dans les versions côte à côte de Visual Studio, procédez comme suit :  
  
-   Vous devez déterminer quelle stratégie de mise en œuvre côte à côte vous souhaitez suivre.  
  
     Pour plus d’informations, consultez [en choisissant entre partagées et des VSPackages avec version](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Le format de fichier solution et projet doit tenir votre stratégie de mise en œuvre.  
  
     Pour plus d’informations, consultez [la mise à niveau des projets personnalisés](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) et [l’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Votre programme d’installation doit gérer votre stratégie de mise en œuvre afin que les composants avec version, ainsi que les composants partagés par toutes les versions, sont correctement installés et inscrits.  
  
     Pour plus d’informations, consultez [l’installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [gestion des composants](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installation d’une version de Visual Studio installe également une version correspondante de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Par exemple, l’installation de Visual Studio 2010 et Visual Studio 2012 sur le même ordinateur installe également les versions 4.0 et 4.5 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], respectivement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Choix entre les VSPackages partagés et à versions gérées](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explique comment résoudre les problèmes de côte à côte dans votre VSPackage.  
  
 [Inscription d’extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Décrit comment votre VSPackage peut enregistrer des associations de fichiers dans un scénario côte à côte.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
