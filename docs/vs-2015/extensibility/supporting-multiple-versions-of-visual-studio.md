---
title: Prise en charge plusieurs Versions de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f68da8f7e397afef82c138af7d5228fe658dbb4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192605"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Prise en charge de plusieurs versions de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le terme *côte à côte* signifie que vous pouvez installer et gérer plusieurs versions d’un produit sur le même ordinateur. Pour les VSPackages, cela signifie que d’un utilisateur peut avoir plusieurs versions de Visual Studio installées sur le même ordinateur. Toutefois, vous ne pouvez avoir des versions côte à côte de vos VSPackages chargées dans une seule version de Visual Studio.  
  
 Avant d’apporter votre VSPackage en mesure d’être chargés dans les versions côte à côte de Visual Studio, procédez comme suit :  
  
-   Vous devez déterminer quelle stratégie de mise en œuvre côte à côte vous souhaitez suivre.  
  
     Pour plus d’informations, consultez [en choisissant entre partagées et des VSPackages avec version](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Vos formats de fichier solution et projet doivent tenir votre stratégie d’implémentation.  
  
     Pour plus d’informations, consultez [la mise à niveau des projets personnalisés](../misc/upgrading-custom-projects.md) et [l’inscription des Extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Votre programme d’installation doit gérer votre stratégie d’implémentation afin que les composants versionnés, ainsi que les composants partagés par toutes les versions, sont correctement installés et inscrits.  
  
     Pour plus d’informations, consultez [installation les VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et également [gestion des composants](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installation d’une version de Visual Studio installe également une version correspondante de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Par exemple, l’installation de Visual Studio 2010 et Visual Studio 2012 sur le même ordinateur installe également les versions 4.0 et 4.5 de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], respectivement.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Choix entre les VSPackages partagés et à versions gérées](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explique comment résoudre les problèmes de côte à côte dans votre VSPackage.  
  
 [Inscription d’extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Décrit la manière dont votre VSPackage peut inscrire des associations de fichiers dans un scénario côte à côte.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Installation de VSPackages](../misc/installing-vspackages.md)  
 Explique comment générer et installer des VSpackages et prendre en charge les utilisateurs qui exécutent plusieurs versions de Visual Studio en même temps.

