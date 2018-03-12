---
title: "Éléments de conception de VSPackage contrôle source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 234346aba360d70d3bbc673067d2634a5112d0f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-design-elements"></a>Éléments de conception de VSPackage de contrôle de source
Les rubriques de cette section décrivent la structure du contrôle de code source VSPackage doit implémenter pour l’intégration en profondeur. Il répertorie également les interfaces et les services que la contrôle de code source VSPackage peuvent implémenter les interfaces et les services du contrôle de code source VSPackage peut utiliser à partir d’autres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composants pour prendre en charge de sa source de contrôlent le modèle et les fonctionnalités.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Structure de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Définit la structure du contrôle source VSPackage.  
  
 [Interfaces et les Services associés](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Répertorie les interfaces de package liés de contrôle source et les services.  
  
 [Services fournis](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Décrit le service de contrôle de code source fourni par le contrôle de code source VSPackage.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Explique comment créer un contrôle de source de package Visual Studio qui fournit les fonctionnalités de contrôle de code source non seulement, mais peut être utilisé pour personnaliser le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur de contrôle de code source.