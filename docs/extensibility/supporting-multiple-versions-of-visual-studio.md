---
title: Soutenir plusieurs versions de Visual Studio (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699474"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Prise en charge de plusieurs versions de Visual Studio
Le terme *côte à côte* signifie que vous pouvez installer et maintenir plusieurs versions d’un produit sur le même ordinateur. Pour VSPackages, cela signifie qu’un utilisateur peut avoir plusieurs versions Visual Studio installées sur le même ordinateur. Cependant, vous ne pouvez pas avoir des versions côte à côte de vos VSPackages chargées dans une seule version de Visual Studio.

 Avant de faire de votre VSPackage en mesure d’être chargé dans les versions côte à côte de Visual Studio, considérez ce qui suit:

- Vous devez déterminer quelle stratégie de mise en œuvre côte à côte vous souhaitez suivre.

   Pour plus d’informations, voir [Choisir entre les VSPackages partagés et versionnés](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Vos formats de fichiers de solutions et de projets doivent s’adapter à votre stratégie de mise en œuvre.

   Pour plus d’informations, voir [Mise à niveau des projets personnalisés](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) et [l’enregistrement des extensions de noms de fichiers pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Votre installateur doit gérer votre stratégie de mise en œuvre afin que les composants versionnés, ainsi que les composants partagés sur toutes les versions, soient correctement installés et enregistrés.

   Pour plus d’informations, voir [Installer VSPackages With Windows Install](../extensibility/internals/installing-vspackages-with-windows-installer.md) et aussi Component [Management](../extensibility/internals/component-management.md).

  > [!NOTE]
  > L’installation d’une version de Visual Studio installe également une version correspondante du cadre .NET. Par exemple, l’installation de Visual Studio 2010 et Visual Studio 2012 sur le même ordinateur installe également les versions 4.0 et 4.5 du cadre .NET, respectivement.

## <a name="in-this-section"></a>Dans cette section
- [Choisir entre VSPackages partagés et versionnés](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Explique comment résoudre les problèmes côte à côte dans votre VSPackage.

- [Enregistrement des extensions de noms de fichiers pour les déploiements côte à côte](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Décrit comment votre VSPackage peut enregistrer des associations de fichiers dans un scénario côte à côte.

## <a name="related-sections"></a>Sections connexes
- [Installation de VSPackages avec Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
