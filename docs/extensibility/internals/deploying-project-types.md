---
title: Déploiement des Types de projet | Documents Microsoft
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
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-project-types"></a>Types de projets de déploiement
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] installe une nouvelle agrégation de type de projet (ProjectAggregator2.dll) et également un package Windows Installer pour la redistribution (ProjectAggregator2.msi). Vous devez utiliser le nouvel aggregator pour les types de projets de code managé. ProjectAggregator2 fonctionne limitations de problèmes rencontrés dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet aggregator qui empêchent les types de projets de code managé de fonctionner correctement. Les étapes suivantes décrivent comment modifier votre VSPackage pour utiliser le nouvel aggregator.  
  
1.  Supprimer le projet NativeHierarchyWrapper de votre solution.  
  
2.  Supprimez les fichiers binaires NativeHierarchyWrapper de votre installation.  
  
3.  Ajoutez ProjectAggregator2.msi à votre configuration.