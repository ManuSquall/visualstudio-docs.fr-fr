---
title: Quand créer des Types de projet | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c99aed424094d21fa1cd84163d5ee36f206fa19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506181"
---
# <a name="when-to-create-project-types"></a>Quand créer des types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [quand créer des Types de projet](https://docs.microsoft.com/visualstudio/extensibility/internals/when-to-create-project-types).  
  
Création d’un nouveau type de projet fournit une base pour la personnalisation [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour vos utilisateurs. Toutefois, la création d’un nouveau type de projet n’est pas requis pour tous les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] personnalisations. Les instructions suivantes devraient vous aider à déterminer si un nouveau type de projet est nécessaire pour votre scénario.  
  
## <a name="create-a-new-project-type"></a>Créer un nouveau Type de projet  
 Vous devez créer un type de projet si vous souhaitez personnaliser [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] d’agir dans une ou plusieurs des manières suivantes :  
  
-   Dans la génération, déploiement, configurations et contrôle de code source.  
  
-   Offre la prise en charge le débogage.  
  
-   Afficher les éléments de projet dans **l’Explorateur de solutions**.  
  
-   Utilisez le **ouvrir un projet** ou **nouveau projet** boîte de dialogue.  
  
-   Prend en charge l’imbrication de projet.  
  
## <a name="extend-an-existing-project-type"></a>Étendre un Type de projet existant  
 Vous souhaiterez peut-être créer un nouveau type de projet que vous pouvez utiliser [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dans les méthodes suivantes pour modifier ou étendre le comportement d’un type de projet existant, par exemple, modifiez le processus de génération pour [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projets :  
  
-   Travailler avec plusieurs fichiers sous la forme d’une seule unité.  
  
-   Afficher un seul fichier comme une hiérarchie de sous-éléments.  
  
-   Afficher un contexte de commande autour des éditeurs.  
  
-   Afficher un contexte de service pour les éditeurs.  
  
## <a name="use-an-existing-project-type"></a>Utiliser un Type de projet existant  
 Création d’un projet n’est parfois pas nécessaire. Le tableau suivant présente les tâches que vous n’êtes pas obligé de créer un type de projet pour.  
  
|Tâche|Description|  
|----------|-----------------|  
|Gestion des commandes|Un VSPackage peut gérer les commandes.|  
|Création d’un éditeur|Éditeurs personnalisés peuvent être inscrits. Pour plus d’informations, consultez [Document Windows et les éditeurs](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propriétaire de windows|Vous pouvez créer des fenêtres Outil et document sans ajouter un nouveau type de projet.|  
|Exposition de propriétés dans la fenêtre Propriétés|Tous les objets peuvent exposer des propriétés.|  
  
## <a name="create-a-project-subtype"></a>Créer un sous-type de projet  
 Vous pouvez utiliser des sous-types de projet pour étendre un type de projet managé sans avoir à créer un nouveau type de projet. Sous-types de projet permettent d’agrégation COM d’étendre des projets managés écrites en Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Avec l’agrégation COM, vous pouvez réutiliser une grande partie de l’implémentation de système de projet managé et toujours personnaliser pour un scénario particulier par le biais d’agrégation et l’utilisation de la prise en charge des interfaces. Pour plus d’informations sur les sous-types de projet, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Windows et les éditeurs](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

