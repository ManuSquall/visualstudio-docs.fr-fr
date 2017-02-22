---
title: "D&#233;terminer s&#39;il faut impl&#233;menter un VSPackage de contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages de contrôle source, à propos des packages de contrôle de code source"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# D&#233;terminer s&#39;il faut impl&#233;menter un VSPackage de contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette section décrit plus en détail les options de plug\-ins de contrôle de code source et du contrôle de code source VSPackages permettant d'étendre les solutions de contrôle de code source et fournit des indications générales à propos de choisir un chemin d'accès approprié d'intégration.  
  
## petite solution de contrôle de code source avec les ressources limitées  
 Si vous avez limité des ressources et ne peut pas être chargé de la charge d'écrire un package de contrôle de code source, vous pouvez créer des connexions API\-basées par plug\-in contrôle de code source.  Cela vous permet d'exécuter côte à côte avec les packages de contrôle de code source, et vous pouvez basculer entre les plug\-ins de contrôle de code source et empaquetez à la demande.  Pour plus d'informations, consultez [L'inscription et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## Grande solution de contrôle de code source avec un ensemble de fonctionnalités riche  
 Si vous souhaitez implémenter une solution de contrôle de code source qui fournit un modèle de contrôle de code source riche qui ne sont pas capturées à l'aide de l'API des plug\-ins de contrôle de code source, vous pouvez considérer un package de contrôle de code source comme un chemin d'accès d'intégration.  Cela s'applique surtout si vous remplaceriez plutôt le package d'adaptateur de contrôle de code source \(qui communique avec le plug\-ins de contrôle de code source et fournit un contrôle de source de base interface utilisateur\) par le vôtre afin de pouvoir gérer les événements de contrôle de code source de façon personnalisée.  Si vous avez déjà un contrôle de code source satisfaisant interface utilisateur et souhaitez conserver cette expérience dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'option de package de contrôle de code source vous permet de faire comme son nom.  Le package de contrôle de code source n'est pas générique et est conçu uniquement pour une utilisation avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.  
  
 Si vous souhaitez implémenter une solution de contrôle de code source qui offre une flexibilité et le contrôle plus riche de la logique de contrôle de code source et de l'interface utilisateur, vous pouvez préférer l'itinéraire d'intégration de package de contrôle de code source.  Vous pouvez effectuer l'une des actions suivantes :  
  
1.  Enregistrez votre propre contrôle de code source VSPackage \(consultez [L'inscription et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)\).  
  
2.  Remplacez le contrôle de code source par défaut interface utilisateur avec votre interface utilisateur personnalisée \(consultez [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\).  
  
3.  Spécifiez les glyphes à utiliser et gérer les événements de glyphe de l'explorateur de solutions \(consultez [Contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md)\).  
  
4.  Événements de sauvegarde de modification de requête de handle et de requête \(consultez [Modifier la requête requête d'enregistrement](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)\).  
  
## Voir aussi  
 [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)