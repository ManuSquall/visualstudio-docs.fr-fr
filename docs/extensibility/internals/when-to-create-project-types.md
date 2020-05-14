---
title: Quand créer des types de projets Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703429"
---
# <a name="when-to-create-project-types"></a>Quand créer des types de projets
La création d’un nouveau type [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projet fournit une base pour personnaliser vos utilisateurs. Cependant, la création d’un nouveau [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] type de projet n’est pas nécessaire pour toutes les personnalisations. Les lignes directrices suivantes devraient vous aider à déterminer si un nouveau type de projet est nécessaire pour votre scénario.

## <a name="create-a-new-project-type"></a>Créer un nouveau type de projet
 Vous devez créer un type de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projet si vous souhaitez personnaliser pour agir d’une ou plusieurs des façons suivantes :

- Participez à la construction, au déploiement, aux configurations et au contrôle des sources.

- Offrez un soutien de débogage.

- Afficher les éléments du projet dans **Solution Explorer**.

- Utilisez la **boîte de** dialogue Open Project ou New **Project.**

- Soutenir la nidification du projet.

## <a name="extend-an-existing-project-type"></a>Étendre un type de projet existant
 Vous pouvez créer un nouveau type [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projet qui peut utiliser de la manière suivante pour modifier ou étendre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] le comportement d’un type de projet existant, par exemple, modifier le processus de construction pour les projets :

- Travailler avec plusieurs fichiers comme une seule unité.

- Affichez un seul fichier comme une hiérarchie de sous-éléments.

- Affichez un contexte de commande autour des éditeurs.

- Afficher un contexte de service pour les éditeurs.

## <a name="use-an-existing-project-type"></a>Utiliser un type de projet existant
 La création d’un nouveau projet n’est parfois pas nécessaire. Le tableau suivant montre les tâches pour lesquelles vous n’avez pas à créer un type de projet.

|Tâche|Description|
|----------|-----------------|
|Commande de manutention|N’importe quel VSPackage peut gérer les commandes.|
|Construire un éditeur|Les éditeurs personnalisés peuvent être enregistrés. Pour plus d’informations, voir [Document Windows et Editors](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Fenêtres de possession|Vous pouvez créer à la fois des fenêtres d’outils et de documents sans ajouter un nouveau type de projet.|
|Exposer les propriétés dans la fenêtre Propriétés|Tous les objets peuvent exposer des propriétés.|

## <a name="create-a-project-subtype"></a>Créer un sous-type de projet
 Vous pouvez utiliser des sous-types de projets pour étendre un type de projet géré sans avoir à créer un nouveau type de projet. Les sous-types de projets utilisent l’agrégation [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]COM pour étendre les projets gérés écrits dans Microsoft ou . Avec l’agrégation COM, vous pouvez réutiliser une grande partie de la mise en œuvre du système de projet géré tout en s’personnalisant pour un scénario particulier grâce à l’agrégation et à l’utilisation d’interfaces de support. Pour plus d’informations sur les sous-types de projets, voir [Les sous-types du projet](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Voir aussi
- [Document Windows et editors](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
