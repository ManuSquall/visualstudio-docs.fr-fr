---
title: Quand créer des types de projet | Microsoft Docs
description: Découvrez comment déterminer si un nouveau type de projet est requis pour la personnalisation de Visual Studio pour vos utilisateurs.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 458ca77ebcd8017b9834a8925edec255ca04cc13
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487827"
---
# <a name="when-to-create-project-types"></a>Quand créer des types de projets
La création d’un nouveau type de projet fournit une base de personnalisation [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour vos utilisateurs. Toutefois, la création d’un nouveau type de projet n’est pas obligatoire pour toutes les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personnalisations. Les instructions suivantes doivent vous aider à déterminer si un nouveau type de projet est requis pour votre scénario.

## <a name="create-a-new-project-type"></a>Créer un nouveau type de projet
 Vous devez créer un type de projet si vous souhaitez personnaliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour agir d’une ou plusieurs des manières suivantes :

- Participez à la génération, au déploiement, aux configurations et au contrôle de code source.

- Offre une prise en charge du débogage.

- Affichez les éléments de projet dans **Explorateur de solutions**.

- Utilisez la boîte de dialogue **ouvrir un projet** ou **nouveau projet** .

- Prendre en charge l’imbrication de projet.

## <a name="extend-an-existing-project-type"></a>Étendre un type de projet existant
 Vous pouvez créer un nouveau type de projet qui peut être utilisé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de l’une des manières suivantes pour modifier ou étendre le comportement d’un type de projet existant, par exemple, en modifiant le processus de génération pour les [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets :

- Utilisez plusieurs fichiers en tant qu’unité unique.

- Affichez un seul fichier sous la forme d’une hiérarchie de sous-éléments.

- Affichez un contexte de commande autour des éditeurs.

- Affichez un contexte de service pour les éditeurs.

## <a name="use-an-existing-project-type"></a>Utiliser un type de projet existant
 Il n’est pas toujours nécessaire de créer un projet. Le tableau suivant répertorie les tâches pour lesquelles vous n’avez pas besoin de créer de type de projet.

|Tâche|Description|
|----------|-----------------|
|Gestion des commandes|N’importe quel VSPackage peut gérer des commandes.|
|Génération d’un éditeur|Les éditeurs personnalisés peuvent être inscrits. Pour plus d’informations, consultez [fenêtres de document et éditeurs](/previous-versions/bb165691(v=vs.100)).|
|Fenêtres propriétaires|Vous pouvez créer des fenêtres d’outils et de documents sans ajouter un nouveau type de projet.|
|Exposition des propriétés dans le Fenêtre Propriétés|Tous les objets peuvent exposer des propriétés.|

## <a name="create-a-project-subtype"></a>Créer un sous-type de projet
 Vous pouvez utiliser des sous-types de projet pour étendre un type de projet managé sans avoir à créer un nouveau type de projet. Les sous-types de projet utilisent l’agrégation COM pour étendre les projets managés écrits dans Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Avec l’agrégation COM, vous pouvez réutiliser la majeure partie de l’implémentation du système de projet géré et toujours personnaliser pour un scénario particulier par le biais de l’agrégation et de l’utilisation des interfaces de prise en charge. Pour plus d’informations sur les sous-types de projet, consultez sous- [types de projet](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Voir aussi
- [Fenêtres de document et éditeurs](/previous-versions/bb165691(v=vs.100))
- [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)