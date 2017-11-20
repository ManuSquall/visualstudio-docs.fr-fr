---
title: "Déploiement des Types de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7673839e44e913d7d0a219400142fe7e6a0b95e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-project-types"></a>Types de projets de déploiement
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]installe une nouvelle agrégation de type de projet (ProjectAggregator2.dll) et également un package Windows Installer pour la redistribution (ProjectAggregator2.msi). Vous devez utiliser le nouvel aggregator pour les types de projets de code managé. ProjectAggregator2 fonctionne limitations de problèmes rencontrés dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet aggregator qui empêchent les types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel aggregator.  
  
1.  Supprimer le projet NativeHierarchyWrapper de votre solution.  
  
2.  Supprimez les fichiers binaires NativeHierarchyWrapper de votre installation.  
  
3.  Ajoutez ProjectAggregator2.msi à votre configuration.