---
title: "Architecture de plug-in de contr&#244;le de code source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, architecture"
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Architecture de plug-in de contr&#244;le de code source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez ajouter la prise en charge de contrôle de code source à l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en implémentant et en attachant un plug\-in contrôle de code source.  L'IDE se connecte au plug\-in contrôle de code source via l'API bien définie de plug\-in contrôle de code source.  L'IDE expose les fonctionnalités de contrôle de version du système de contrôle de code source en fournissant une \(UI\) interface utilisateur qui se compose des barres d'outils et les commandes de menu.  Le plug\-in contrôle de code source implémente les fonctionnalités de contrôle de code source.  
  
## Ressources de plug\-in contrôle de code source  
 Le plug\-in contrôle de code source fournit des ressources pour vous aider à créer et connecter votre application de versioning à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.  Le plug\-in contrôle de code source contient la spécification d'API qui doit être implémentée par un plug\-in contrôle de code source afin qu'il puisse être intégré dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.  Elle contient également un exemple de code \(écrit en C\+\+\) qui implémente une implémentation montrante du plug\-in du contrôle de code source squelette des fonctions essentielles conformes avec l'API du plug\-in contrôle de code source.  
  
 La spécification du plug\-in d'API de contrôle de code source vous permet de tirer parti tout système de contrôle de code source de votre choix si vous créez une DLL de contrôle de code source avec l'ensemble requis de fonctions implémentées conformément à l'API de plug\-in contrôle de code source.  
  
## Composants  
 Le package d'adaptateur de contrôle de code source dans le diagramme est le composant de l'IDE qui convertit la requête du client pour une opération de contrôle de code source en appel de fonction pris en charge par le plug\-in contrôle de code source.  Pour que cela se produise, l'IDE et le plug\-in contrôle de code source doivent avoir une boîte de dialogue efficace qui passe les informations dans les deux sens entre l'IDE et le plug\-in.  Pour que ce dialogue n'a lieu, tous deux doivent parler le même langage.  L'API des plug\-ins de contrôle de code source présentées dans cette documentation est le vocabulaire commun pour cet échange.  
  
 ![Diagramme de l'architecture du contrôle du code source](~/docs/extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs\_sccsdk\_plug\_in\_arch")  
Architecture de diagrammes d'apparence d'interaction plug\-in entre visual studio et du contrôle de code source  
  
 Comme illustré dans le diagramme d'architecture, le shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , étiqueté comme VS le shell dans le diagramme, héberge des projets de travail et les composants associés de l'utilisateur, tels que les éditeurs et l'explorateur de solutions.  Le package d'adaptateur de contrôle de code source gère l'interaction entre l'IDE et le plug\-in contrôle de code source.  le package d'adaptateur de contrôle de code source fournit son propre contrôle de code source interface utilisateur.  Il s'agit du niveau supérieur interface utilisateur avec lequel l'utilisateur interagit pour initialiser et définir la portée d'une opération de contrôle de code source.  
  
 Le plug\-in contrôle de code source peut avoir son propre interface utilisateur, composée de deux parties comme indiqué dans l'illustration.  La région étiquetée « fournisseur interface utilisateur » représente les éléments de l'interface utilisateur personnalisés que vous pouvez, en tant que créateur du plug\-in du contrôle de code source, fournissez.  Celles\-ci sont affichées directement par le plug\-in contrôle de code source lorsque l'utilisateur appelle une opération de contrôle de code source avancée.  La région étiquetée « programme d'assistance interface utilisateur » est un ensemble de fonctionnalités du plug\-in interface utilisateur du contrôle de code source qui sont indirectement appelées à travers l'IDE.  Le plug\-in contrôle de code source passe les messages Interface utilisateur\-mis en rapport avec l'IDE via les fonctions de rappel spéciales fournies par l'IDE.  Le programme d'assistance interface utilisateur facilite plus d'intégration transparente avec l'IDE \(souvent à l'aide d'un bouton d' **Avancé** \) et fournit donc une expérience plus unifiée.  
  
 Un plug\-in contrôle de code source ne peut pas apporter de modifications à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écosser et, par conséquent, au package ou au contrôle de code source interface utilisateur d'adaptateur de contrôle de code source fourni par l'IDE.  Il doit avoir une utilisation maximale de la possibilité offerte par le biais de l'implémentation des fonctions d'API du plug\-in de autre contrôle de code source contribuant à une expérience intégrée pour l'utilisateur final.  La section de la documentation du plug\-in d'API de contrôle de code source inclut les informations pour certaines fonctions avancées de plug\-in contrôle de code source.  Pour exploiter ces fonctionnalités, le plug\-in contrôle de code source doit déclarer ses fonctionnalités avancées à l'IDE pendant l'initialisation, et il doit implémenter des fonctions avancées spécifique pour chaque fonction.  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md)   
 [Glossaire](../../extensibility/source-control-plug-in-glossary.md)   
 [Création d'un contrôle de Source de plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)