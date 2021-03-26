---
title: Prise en charge de plusieurs versions de Visual Studio | Microsoft Docs
description: Découvrez comment vous pouvez prendre en charge plusieurs versions de Visual Studio, avec les VSPackages capables de se charger dans différentes versions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d455ebf18ee8817e2adac2fa266592594ca7e6c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056101"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Prise en charge de plusieurs versions de Visual Studio
Le terme « *côte à côte* » signifie que vous pouvez installer et gérer plusieurs versions d’un produit sur le même ordinateur. Pour les VSPackages, cela signifie qu’un utilisateur peut avoir plusieurs versions de Visual Studio installées sur le même ordinateur. Toutefois, les versions côte à côte de vos VSPackages ne peuvent pas être chargées dans une seule version de Visual Studio.

 Avant de pouvoir charger votre VSPackage dans des versions côte à côte de Visual Studio, tenez compte des points suivants :

- Vous devez déterminer la stratégie d’implémentation côte à côte que vous souhaitez suivre.

   Pour plus d’informations, consultez [Choosing Between Shared and Versioned VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Vos formats de fichiers de projet et de solution doivent correspondre à votre stratégie d’implémentation.

   Pour plus d’informations, consultez [mise à niveau de projets personnalisés](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) et [inscription d’extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Votre programme d’installation doit gérer votre stratégie d’implémentation afin que les composants avec version, ainsi que les composants partagés sur toutes les versions, soient correctement installés et inscrits.

   Pour plus d’informations, consultez [installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) et [gestion des composants](../extensibility/internals/component-management.md).

  > [!NOTE]
  > L’installation d’une version de Visual Studio installe également une version correspondante du .NET Framework. Par exemple, l’installation de Visual Studio 2010 et de Visual Studio 2012 sur le même ordinateur installe également les versions 4,0 et 4,5 du .NET Framework, respectivement.

## <a name="in-this-section"></a>Dans cette section
- [Choix entre les VSPackages partagés et les VSPackages avec version](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Explique comment résoudre les problèmes côte à côte dans votre VSPackage.

- [Inscription des extensions de nom de fichier pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Décrit comment votre VSPackage peut inscrire des associations de fichiers dans un scénario côte à côte.

## <a name="related-sections"></a>Sections connexes
- [Installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
