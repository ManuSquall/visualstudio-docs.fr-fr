---
title: "Essentials de l&#39;int&#233;gration de contr&#244;le de code source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Intégration du contrôle de code source, essentials"
  - "Intégration du contrôle de code source, vue d'ensemble"
  - "Essentials, intégration du contrôle de code Source"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Essentials de l&#39;int&#233;gration de contr&#244;le de code source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types d'intégration du contrôle de code source : un plug\-in contrôle de code source qui fournit les fonctionnalités de base et est généré à l'aide de l'API des plug\-ins de contrôle de code source \(anciennement connue sous le nom de API de MSSCCI\), et une solution VSPackage\-basée d'intégration de contrôle de code source qui fournit une fonctionnalité plus fiable.  
  
## Plug\-in contrôle de code source  
 Un plug\-in contrôle de code source est écrit sous la forme d'une DLL qui implémente l'API de plug\-in contrôle de code source.  La fonctionnalité d'intégration d'alignement et de contrôle de code source est fournie via l'API.  il est plus facile implémenter cette approche qu'un contrôle de code source VSPackage, et elle utilise l'interface utilisateur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(UI\) pour la plupart des opérations de contrôle de code source.  
  
 Pour implémenter un plug\-in contrôle de code source en utilisant l'API des plug\-ins de contrôle de code source, procédez comme suit :  
  
1.  Créez une DLL qui implémente des fonctions spécifiées dans [Plug\-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md).  
  
2.  Enregistrez la DLL en faisant les entrées du Registre appropriées, comme décrit dans [Comment : installer un plug\-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Créez un programme d'assistance interface utilisateur et affichez \-le lorsque vous êtes invité par le package d'adaptateur de contrôle de code source \(le composant de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] qui gère les fonctionnalités de contrôle de code source pour le plug\-ins de contrôle de code source\).  
  
 Pour plus d'informations, consultez [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## contrôle de code source VSPackage  
 Une implémentation d'un VSPackage de contrôle de code source vous permet de développer un remplacement personnalisé pour le contrôle de code source interface utilisateur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Cette approche fournit un contrôle complet sur l'intégration du contrôle de code source, mais elle requiert que vous de fournir les éléments de l'interface utilisateur et d'implémenter les interfaces du contrôle de code source managé qui seraient fournis sous l'approche de plug\-in.  
  
 pour implémenter un contrôle de code source VSPackage, vous devez :  
  
1.  créez et enregistrez votre propre contrôle de code source VSPackage, comme décrit dans [L'inscription et la sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Remplacez le contrôle de code source par défaut interface utilisateur avec votre interface utilisateur personnalisée.  Consultez [Interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Spécifiez les glyphes à utiliser, et gérer les événements de glyphe de **Explorateur de solutions** .  Consultez [Contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  La modification de requête de handle et la requête enregistrent des événements, comme indiqué dans [Modifier la requête requête d'enregistrement](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Pour plus d'informations, consultez [Création d'un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## Voir aussi  
 [Vue d'ensemble](../../extensibility/internals/source-control-integration-overview.md)   
 [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Création d'un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md)