---
title: Contexte du projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725772"
---
# <a name="project-context"></a>Contexte de projet
Quand l’utilisateur ajoute ou travaille avec des projets et des éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer comment diverses opérations doivent être exécutées.

 En règle générale, les fichiers sont les objets de projet standard que l’utilisateur crée explicitement en sélectionnant la commande **nouveau projet** ou rend disponible en sélectionnant la commande **ouvrir un projet** dans le menu **fichier** . Dans ces cas, les fichiers sont créés et ouverts dans le contexte d’un projet et le type de projet définit le contexte pour la modification du document.

 Certains projets fournissent un contexte très riche. Par exemple, le projet gère une connexion de base de données à portée de projet, d’espace de noms de programmation ou de projet pour la liaison de données. L’utilisateur peut souvent ouvrir des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, tel qu’un élément de projet affiché dans Explorateur de solutions.

 À d’autres moments, le contexte de projet d’un élément n’est pas explicitement spécifié. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant la commande **ouvrir un fichier existant** dans le menu **fichier** , lorsque le débogueur opère sur un fichier, ou lorsque l’utilisateur clique sur la commande **Rechercher dans les fichiers** dans la  **Boîte de dialogue Rechercher et remplacer** . Pour gérer ces situations, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> pour gérer le processus de recherche du meilleur projet pour ouvrir un document.

## <a name="see-also"></a>Voir aussi
- [Priorité de projet](../../extensibility/internals/project-priority.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)