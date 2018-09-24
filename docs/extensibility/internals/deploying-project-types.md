---
title: Déploiement des Types de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bed37260925d4961ed5b5b7d3e69d55169444ad
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497899"
---
# <a name="deploy-project-types"></a>Déployer des types de projets
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installe une nouvelle agrégation de type de projet (*ProjectAggregator2.dll*) et également un package de programme d’installation de Windows pour la redistribution (*ProjectAggregator2.msi*). Vous devez utiliser le nouvel aggregator pour les types de projets de code managé. ProjectAggregator2 articulé autour des limitations dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet aggregator qui empêche des types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel aggregator.  
  
1.  Supprimer le projet NativeHierarchyWrapper de votre solution.  
  
2.  Supprimer les fichiers binaires NativeHierarchyWrapper à partir de votre installation.  
  
3.  Ajouter *ProjectAggregator2.msi* à votre installation.