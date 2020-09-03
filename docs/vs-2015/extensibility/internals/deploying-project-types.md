---
title: Déploiement des types de projets | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196880"
---
# <a name="deploying-project-types"></a>Déploiement des types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] installe une nouvelle agrégation de type projet (ProjectAggregator2.dll) et également un package Windows Installer pour la redistribution (ProjectAggregator2.msi). Vous devez utiliser le nouvel agrégateur pour les types de projets de code managé. ProjectAggregator2 contourne les limitations de l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] agrégateur de projet qui empêchent le bon fonctionnement des types de projets de code managé. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel agrégateur.  
  
1. Supprimez le projet NativeHierarchyWrapper de votre solution.  
  
2. Supprimez tous les fichiers binaires NativeHierarchyWrapper de votre installation.  
  
3. Ajoutez ProjectAggregator2.msi à votre installation.
