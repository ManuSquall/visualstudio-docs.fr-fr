---
title: Déterminer s’il faut implémenter un VSPackage de contrôle de code Source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ed78f8245479edfaa5e87c22e6651c867d96f98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914462"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Déterminer s’il faut implémenter un VSPackage de contrôle de code source
Cette section décrit plus en détail les choix de plug-ins de contrôle de code source et de contrôle de code source VSPackages pour l’extension de contrôle de code source des solutions et donne des indications générales sur le choix d’un chemin d’accès de l’intégration approprié.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solution de contrôle de source de petits avec des ressources limitées  
 Si vous avez des ressources limitées et ne peut pas être surchargé par la surcharge de l’écriture d’un package de contrôle de code source, vous pouvez créer des plug-ins basée sur les API de plug-in de contrôle de Source. Ainsi, vous permettent de travailler côte à côte avec les packages de contrôle de code source, et vous pouvez basculer entre les plug-ins de contrôle de code source et les packages à la demande. Pour plus d’informations, consultez [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solution de contrôle de source de grande taille avec un ensemble complet de fonctionnalités  
 Si vous souhaitez implémenter une solution de contrôle de source qui fournit un modèle de contrôle de source riche qui n’est pas correctement capturé à l’aide de l’API de plug-in de contrôle de Source, vous pouvez envisager un package de contrôle de code source en tant que le chemin d’accès de l’intégration. Cela s’applique en particulier si vous devez remplacer plutôt le Package de l’adaptateur de contrôle de code Source (qui communique avec les plug-ins de contrôle de code source et fournit un interface utilisateur du contrôle de source de base) par les vôtres afin que vous pouvez gérer les événements de contrôle de source de manière personnalisée. Si vous disposez déjà d’une source satisfaisante contrôler l’interface utilisateur et souhaitez conserver cette expérience dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l’option de package de contrôle de code source vous permet de faire exactement cela. Le package de contrôle de code source n’est pas générique et est conçu uniquement pour une utilisation avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Si vous souhaitez implémenter une solution de contrôle de source qui fournit une flexibilité et contrôle plus riche sur l’interface utilisateur et la logique de contrôle de code source, vous pouvez préférer l’itinéraire de l’intégration de package de contrôle source. Vous pouvez :  
  
1.  Inscrire votre propre contrôle de source de package Visual Studio (consultez [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Remplacez le contrôle de code source par défaut l’interface utilisateur avec votre interface utilisateur personnalisée (consultez [l’interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Spécifiez des glyphes à utiliser et gérer les événements de glyphe de l’Explorateur de solutions (voir [contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Gérer les événements de modification de la requête et d’enregistrement des requêtes (consultez [modifier les requêtes d’enregistrement des requêtes](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un contrôle de source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)