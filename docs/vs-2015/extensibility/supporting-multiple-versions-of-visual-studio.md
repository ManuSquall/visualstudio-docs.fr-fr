---
title: Prise en charge de plusieurs versions de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839282"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Prise en charge de plusieurs versions de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le terme « *côte à côte* » signifie que vous pouvez installer et gérer plusieurs versions d’un produit sur le même ordinateur. Pour les VSPackages, cela signifie qu’un utilisateur peut avoir plusieurs versions de Visual Studio installées sur le même ordinateur. Toutefois, les versions côte à côte de vos VSPackages ne peuvent pas être chargées dans une seule version de Visual Studio.

 Avant de pouvoir charger votre VSPackage dans des versions côte à côte de Visual Studio, tenez compte des points suivants :

- Vous devez déterminer la stratégie d’implémentation côte à côte que vous souhaitez suivre.

     Pour plus d’informations, consultez [Choosing Between Shared and Versioned VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Vos formats de fichiers de projet et de solution doivent correspondre à votre stratégie d’implémentation.

     Pour plus d’informations, consultez [mise à niveau de projets personnalisés](../misc/upgrading-custom-projects.md) et [inscription d’extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Votre programme d’installation doit gérer votre stratégie d’implémentation afin que les composants avec version, ainsi que les composants partagés sur toutes les versions, soient correctement installés et inscrits.

     Pour plus d’informations, consultez [installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [gestion des composants](../extensibility/internals/component-management.md).

    > [!NOTE]
    > L’installation d’une version de Visual Studio installe également une version correspondante du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Par exemple, l’installation de Visual Studio 2010 et de Visual Studio 2012 sur le même ordinateur installe également les versions 4,0 et 4,5 du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , respectivement.

## <a name="in-this-section"></a>Dans cette section
 [Choix entre les VSPackages partagés et les VSPackages avec version](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Explique comment résoudre les problèmes côte à côte dans votre VSPackage.

 [Inscription des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Décrit comment votre VSPackage peut inscrire des associations de fichiers dans un scénario côte à côte.

## <a name="related-sections"></a>Sections connexes
 [Installation de VSPackages](../misc/installing-vspackages.md) Explique comment générer et installer des VSPackages et comment prendre en charge les utilisateurs qui exécutent plusieurs versions de Visual Studio en même temps.
