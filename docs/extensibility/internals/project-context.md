---
title: Contexte du projet | Microsoft Docs
description: Découvrez comment l’IDE de Visual Studio utilise le contexte de projet pour déterminer comment effectuer des opérations lorsque l’utilisateur ajoute ou travaille avec des projets et des éléments de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73e3c8a94607e7e0b31bacddac8e7f19b6139328
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899821"
---
# <a name="project-context"></a>Contexte de projet
Quand l’utilisateur ajoute ou travaille avec des projets et des éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer comment diverses opérations doivent être exécutées.

 En règle générale, les fichiers sont les objets de projet standard que l’utilisateur crée explicitement en sélectionnant la commande **nouveau projet** ou rend disponible en sélectionnant la commande **ouvrir un projet** dans le menu **fichier** . Dans ces cas, les fichiers sont créés et ouverts dans le contexte d’un projet et le type de projet définit le contexte pour la modification du document.

 Certains projets fournissent un contexte très riche. Par exemple, le projet gère une connexion de base de données à portée de projet, d’espace de noms de programmation ou de projet pour la liaison de données. L’utilisateur peut souvent ouvrir des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, tel qu’un élément de projet affiché dans Explorateur de solutions.

 À d’autres moments, le contexte de projet d’un élément n’est pas explicitement spécifié. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant la commande **ouvrir un fichier existant** du menu **fichier** , lorsque le débogueur opère sur un fichier ou lorsque l’utilisateur clique sur la commande **Rechercher dans les fichiers** dans la boîte de dialogue **Rechercher et remplacer** . Pour gérer ces situations, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> pour gérer le processus de recherche du meilleur projet pour ouvrir un document.

## <a name="see-also"></a>Voir aussi
- [Priorité de projet](../../extensibility/internals/project-priority.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
