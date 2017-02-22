---
title: "Quand cr&#233;er des Types de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de projets, les conditions de création"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Quand cr&#233;er des Types de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Créer un type de projet constitue une base pour personnaliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour vos utilisateurs.  Toutefois, la création d'un nouveau type de projet n'est pas requis pour toutes les personnalisations de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Les indications suivantes doivent vous aider à déterminer si un nouveau type de projet est nécessaire à votre scénario.  
  
## Créez un type de projet  
 Vous devez créer un type de projet si vous souhaitez personnaliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour agir d'une des façons suivantes :  
  
-   Participent à la génération, de déploiement, les configurations, et le contrôle de code source.  
  
-   Prise en charge du débogage offrent.  
  
-   éléments de projet d'affichage dans **Explorateur de solutions**.  
  
-   utilisez la boîte de dialogue d' **Ouvrir un projet** ou de **Nouveau projet** .  
  
-   Imbrication de projet de moyenne.  
  
## Étendre un type existant de projet  
 Vous pouvez créer un nouveau type de projet qui peut utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des manières suivantes pour modifier ou étendre le comportement d'un type existant de projet, par exemple, changer le processus de génération pour les projets de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] :  
  
-   Utilisez plusieurs fichiers comme une seule unité.  
  
-   Affichez un fichier unique comme hiérarchie des sous\-éléments.  
  
-   Affichez un contexte de commande autour de les éditeurs.  
  
-   Affichez un contexte de service pour les éditeurs.  
  
## utilisez un type existant de projet  
 créer un nouveau projet n'est parfois pas nécessaire.  Le tableau suivant présente les tâches que vous n'avez pas à créer un type de projet pour.  
  
|Tâche|Description|  
|-----------|-----------------|  
|Gestion des commandes|Tout VSPackage peut gérer des commandes.|  
|générer un éditeur|Des éditeurs personnalisés peuvent être stockés.  Pour plus d'informations, consultez [Document Windows and Editors](http://msdn.microsoft.com/fr-fr/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propriétaire des fenêtres|vous pouvez créer l'outil et les fenêtres de document sans ajouter un nouveau type de projet.|  
|exposer des propriétés dans la fenêtre Propriétés|tous les objets peuvent exposer des propriétés.|  
  
## créez un sous\-type de projet  
 Vous pouvez utiliser des sous\-types de projet pour étendre un type managé de projet sans devoir créer un type de projet.  Sous\-types de projet utilisent le regroupement COM pour étendre des projets managés écrits dans Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Avec une agrégation COM, vous pouvez réutiliser une grande partie de l'implémentation de système de projet managée et personnaliser pour un scénario particulier à travers le regroupement et l'utilisation de prendre en charge les interfaces.  Pour plus d'informations sur des sous\-types de projet, consultez [Sous\-types de projets](../../extensibility/internals/project-subtypes.md).  
  
## Voir aussi  
 [Document Windows and Editors](http://msdn.microsoft.com/fr-fr/603625e1-62b6-413a-bc44-089346e166bc)   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)