---
title: "Déterminer s’il faut implémenter un VSPackage de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 808f2fda26046962eada377f8a204351adef19bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Déterminer s’il faut implémenter un VSPackage de contrôle de code Source
Cette section présente les options de contrôle de code source VSPackages et les plug-ins de contrôle de code source pour l’extension de contrôle de code source des solutions et donne des indications générales sur le choix d’un chemin d’accès de l’intégration approprié.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solution de contrôle de Source de petite avec des ressources limitées  
 Si vous avez des ressources limitées et ne peut pas être surchargé par la charge de l’écriture d’un package de contrôle de code source, vous pouvez créer des plug-ins basée sur les API de plug-in de contrôle de Source. Cela vous permet de travailler côte à côte avec les packages de contrôle de code source, et vous pouvez basculer entre les plug-ins de contrôle de code source et les packages à la demande. Pour plus d’informations, consultez [l’inscription et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solution de contrôle de Source de grande taille avec un ensemble riche de fonctionnalités  
 Si vous souhaitez implémenter une solution de contrôle de source qui fournit un modèle de contrôle de source de riches qui n’est pas correctement capturé à l’aide de l’API de plug-in de contrôle de Source, vous pouvez envisager un package de contrôle de code source en tant que le chemin d’accès de l’intégration. Cela s’applique en particulier si au lieu de cela, vous devez remplacer le Package de l’adaptateur de contrôle de Source (qui communique avec les plug-ins de contrôle de code source et fournit un interface utilisateur du contrôle de source de base) avec vos propres afin que vous pouvez gérer les événements de contrôle de source de manière personnalisée. Si vous avez déjà une bonne source de l’interface utilisateur de contrôler et souhaitez conserver cette expérience dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l’option de package de contrôle de code source vous permet de faire. Le package de contrôle de code source n’est pas générique et est conçu uniquement pour une utilisation avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Si vous souhaitez implémenter une solution de contrôle de source qui fournit une souplesse et un contrôle plus riche sur l’interface utilisateur et la logique de contrôle de code source, vous souhaiterez peut-être l’itinéraire de l’intégration de package de contrôle source. Vous pouvez :  
  
1.  Inscrire votre propre contrôle de code source VSPackage (consultez [l’inscription et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Remplacez le contrôle de code source par défaut l’interface utilisateur de votre interface utilisateur personnalisée (consultez [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Spécifiez les glyphes à utiliser et gérer les événements de glyphe de l’Explorateur de solutions (voir [glyphe contrôle](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Gérer les événements de requête modifier et enregistrer des requêtes (voir [enregistrer de requête modifier requête](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)