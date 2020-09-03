---
title: Détermination de la nécessité d’implémenter un VSPackage de contrôle de code source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196801"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Déterminer s’il faut implémenter un VSPackage de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section décrit les choix des plug-ins de contrôle de code source et des packages de contrôle de code source pour étendre les solutions de contrôle de code source et fournit des instructions générales sur le choix d’un chemin d’intégration approprié.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Petite solution de contrôle de code source avec des ressources limitées  
 Si vous avez des ressources limitées et que vous ne pouvez pas vous occuper de la surcharge liée à l’écriture d’un package de contrôle de code source, vous pouvez créer des plug-ins basés sur des API de plug-in de contrôle de code source. Cela vous permet de travailler côte à côte avec les packages de contrôle de code source, et vous pouvez basculer entre les plug-ins de contrôle de code source et les packages à la demande. Pour plus d’informations, consultez [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solution de contrôle de code source importante avec un ensemble de fonctionnalités enrichi  
 Si vous souhaitez implémenter une solution de contrôle de code source qui fournit un modèle de contrôle de code source riche qui n’est pas capturé correctement à l’aide de l’API de plug-in de contrôle de code source, vous pouvez considérer un package de contrôle de code source comme le chemin d’intégration. Cela s’applique surtout si vous préférez remplacer le package de l’adaptateur de contrôle de code source (qui communique avec les plug-ins de contrôle de code source et fournit une interface utilisateur de contrôle de code source de base) avec les vôtres afin que vous puissiez gérer les événements de contrôle de code source de manière personnalisée. Si vous disposez déjà d’une interface utilisateur de contrôle de code source satisfaisante et que vous souhaitez conserver cette expérience dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , l’option de package de contrôle de code source vous permet de le faire. Le package de contrôle de code source n’est pas générique et est conçu uniquement pour être utilisé avec l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Si vous souhaitez implémenter une solution de contrôle de code source qui offre une flexibilité et un contrôle plus riche de la logique et de l’interface utilisateur du contrôle de code source, vous préférerez peut-être l’itinéraire d’intégration du package de contrôle de code source. Vous pouvez :  
  
1. Inscrivez votre propre VSPackage de contrôle de code source (voir [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Remplacez l’interface utilisateur du contrôle de code source par défaut par votre interface utilisateur personnalisée (voir [interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Spécifiez les glyphes à utiliser et gérez les événements de glyphes Explorateur de solutions (consultez [contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Gérez les événements de modification de requête et d’enregistrement des requêtes (voir [requête modifier la requête enregistrer](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
