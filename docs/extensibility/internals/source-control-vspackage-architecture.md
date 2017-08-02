---
title: "Architecture du contr&#244;le de code source VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages de contrôle de code source, architecture"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Architecture du contr&#244;le de code source VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un package de contrôle de code source est un VSPackage qui utilise les services que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE fournit.  En retour, un package de contrôle de code source utilise sa fonctionnalité en tant que service de contrôle de code source.  En outre, un package de contrôle de code source est une alternative plus flexible qu'un plug\-in contrôle de code source pour intégrer le contrôle de code source dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Un plug\-in contrôle de code source qui implémente l'API des plug\-ins de contrôle de code source est conforme à un contrat strict.  par exemple, un plug\-in ne peut pas remplacer l'interface utilisateur par défaut de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(UI\).  En outre, l'API des plug\-ins de contrôle de code source ne permet pas à un plug\-in d'implémenter son propre modèle de contrôle de code source.  Un package de contrôle de code source, toutefois, surmonte les deux restrictions.  Un package de contrôle de code source a un contrôle complet sur l'expérience de contrôle de code source d'un utilisateur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  En outre, un package de contrôle de code source peut utiliser son propre modèle et logique de contrôle de code source ; elle peut définir toutes les interfaces utilisateur contrôle\-mises en relation par source.  
  
## composants de package de contrôle de code source  
 Comme illustré dans le diagramme d'architecture, un composant de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nommé le stub de contrôle de code source est un VSPackage qui intègre un package de contrôle de code source avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 le stub de contrôle de code source gère les tâches suivantes.  
  
-   Le fournit une interface utilisateur commune requis pour l'inscription de package de contrôle de code source.  
  
-   charge un package de contrôle de code source.  
  
-   définit un package de contrôle de code source comme actif\/inactif.  
  
 Le stub de contrôle de code source recherche le service actif pour le package de contrôle de code source et route tous les appels de service entrants IDE à ce package.  
  
 le package d'adaptateur de contrôle de code source est un package de contrôle de code source spécial que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit.  Ce package est le composant central pour prendre en charge le plug\-ins de contrôle de code source en fonction de l'API de plug\-in contrôle de code source.  Lorsqu'un plug\-in contrôle de code source est le plug\-in actif, le stub de contrôle de code source envoie ses événements au package d'adaptateur de contrôle de code source.  Ensuite, le package d'adaptateur de contrôle de code source communique avec le plug\-in contrôle de code source à l'aide de l'API des plug\-ins de contrôle de code source et fournit également une valeur par défaut interface utilisateur commune pour tous les plug\-ins de contrôle de code source.  
  
 Lorsqu'un package de contrôle de code source est le package actif, en revanche, le stub de contrôle de code source communique directement avec le package à l'aide de les interfaces de package de contrôle de code source de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .  Le package de contrôle de code source est responsable de l'hébergement de son propre contrôle de code source interface utilisateur.  
  
 ![Graphique de l'architecture des contrôles de code source](~/docs/extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Pour un package de contrôle de code source, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne fournit pas le code du contrôle de code source ou d'une API pour l'intégration.  Comparons \-la à l'approche présentées dans [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md) où le plug\-in contrôle de code source doit implémenter un ensemble rigide de fonctions et de rappels.  
  
 Comme tout VSPackage, un package de contrôle de code source est un objet COM qui peut être créé à l'aide de `CoCreateInstance`.  Le VSPackage se met à la disposition [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Lorsqu'une instance créée, un VSPackage reçoit un pointeur de site et une interface d'<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> qui fournit l'accès d'un VSPackage aux services et les interfaces disponibles dans l'IDE.  
  
 Écriture d'un package VSPackage\-basé de contrôle de code source requiert une compétence de programmation plus avancée d'écrire un plug\-in API\-basé par plug\-in contrôle de code source.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)