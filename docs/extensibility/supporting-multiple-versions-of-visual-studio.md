---
title: "Prise en charge de plusieurs Versions de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Prise en charge de plusieurs versions de Visual Studio"
  - "VSPackages, compatibilité côte-à"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Prise en charge de plusieurs Versions de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le terme *côte\-à\-côte* signifie que vous pouvez installer et gérer plusieurs versions d'un produit sur le même ordinateur. Pour les packages VS, cela signifie qu'un utilisateur peut avoir plusieurs versions de Visual Studio installées sur le même ordinateur. Toutefois, vous ne pouvez avoir des versions côte à côte de vos packages VS chargés dans une seule version de Visual Studio.  
  
 Avant d'effectuer votre VSPackage puissent être chargées dans les versions côte à côte de Visual Studio, procédez comme suit :  
  
-   Vous devez déterminer quelle stratégie de mise en œuvre côte à côte vous voulez suivre.  
  
     Pour plus d'informations, consultez [Choix entre les packages VS partagés et version](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Le format de fichier solution et projet doit tenir votre stratégie de mise en œuvre.  
  
     Pour plus d’informations, consultez [Mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md) et [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Votre programme d'installation doit gérer votre stratégie de mise en œuvre afin que les composants versionnés, ainsi que les composants partagés par toutes les versions, sont correctement installés et inscrits.  
  
     Pour plus d'informations, consultez [Installation de packages VS avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [Gestion des composants](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installation d'une version de Visual Studio installe également une version correspondante de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Par exemple, l'installation de Visual Studio 2010 et Visual Studio 2012 sur le même ordinateur installe également les versions 4.0 et 4.5 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], respectivement.  
  
## Dans cette section  
 [Choix entre les packages VS partagés et version](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explique comment résoudre des problèmes dans votre package VS côte à côte.  
  
 [L’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Décrit comment votre VSPackage peut inscrire associations de fichiers dans un scénario côte à côte.  
  
## Rubriques connexes  
 [Installation de VSPackages](../misc/installing-vspackages.md)  
 Explique comment générer et installer les packages VS et prendre en charge les utilisateurs qui exécutent plusieurs versions de Visual Studio en même temps.