---
title: Quand créer des Types de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 682fc88fb616fbe2617fe6d336a35bf6fbc30e9f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938632"
---
# <a name="when-to-create-project-types"></a>Quand créer des types de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
|Création d’un éditeur|Éditeurs personnalisés peuvent être inscrits. Pour plus d’informations, consultez [Document Windows et les éditeurs](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propriétaire de windows|Vous pouvez créer des fenêtres Outil et document sans ajouter un nouveau type de projet.|  
|Exposition de propriétés dans la fenêtre Propriétés|Tous les objets peuvent exposer des propriétés.|  
  
## <a name="create-a-project-subtype"></a>Créer un sous-type de projet  
 Vous pouvez utiliser des sous-types de projet pour étendre un type de projet managé sans avoir à créer un nouveau type de projet. Sous-types de projet permettent d’agrégation COM d’étendre des projets managés écrites en Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Avec l’agrégation COM, vous pouvez réutiliser une grande partie de l’implémentation de système de projet managé et toujours personnaliser pour un scénario particulier par le biais d’agrégation et l’utilisation de la prise en charge des interfaces. Pour plus d’informations sur les sous-types de projet, consultez [sous-types de projet](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Windows et les éditeurs](http://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
