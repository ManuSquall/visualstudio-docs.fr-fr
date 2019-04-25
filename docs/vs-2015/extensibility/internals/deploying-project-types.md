---
title: Déploiement des Types de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076470"
---
# <a name="deploying-project-types"></a>Déploiement des types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] installe une nouvelle agrégation de type de projet (ProjectAggregator2.dll) et également un package de programme d’installation de Windows pour la redistribution (ProjectAggregator2.msi). Vous devez utiliser le nouvel aggregator pour les types de projets de code managé. ProjectAggregator2 fonctionne limitations des solutions de contournement la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projet aggregator empêcher des types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel aggregator.  
  
1. Supprimer le projet NativeHierarchyWrapper de votre solution.  
  
2. Supprimer les fichiers binaires NativeHierarchyWrapper à partir de votre installation.  
  
3. Ajoutez ProjectAggregator2.msi à votre installation.
