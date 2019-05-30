---
title: Contexte de projet | Microsoft Docs
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
ms.openlocfilehash: 175ee37628b1794377a6b4e9e94cef52466cd291
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328358"
---
# <a name="project-context"></a>Contexte de projet
Lorsque l’utilisateur ajoute ou fonctionne avec les projets et éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer la manière dont les différentes opérations doivent être effectuées.

 En règle générale, les fichiers sont les objets de projet standard créées par l’utilisateur explicitement en sélectionnant le **nouveau projet** commande ou met à disposition en sélectionnant le **ouvrir un projet** commande sur le  **Fichier** menu. Dans ces cas, les fichiers sont créés et ouverts dans le contexte d’un projet et le type de projet définit le contexte de modification du document.

 Certains projets fournissent un contexte très riche. Par exemple, le projet gère un espace de noms à portée de projet, par programme ou d’une connexion de base de données à portée de projet pour la liaison de données. L’utilisateur peut ouvrir fréquemment des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, comme un élément de projet affiché dans l’Explorateur de solutions.

 À d’autres moments, le contexte d’un élément de projet n’est pas spécifié explicitement. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant le **ouvrir le fichier existant** commande sur le **fichier** menu, lorsque le débogueur s’exécute sur un fichier, ou lorsque l’utilisateur clique sur le **Recherche dans les fichiers** commande dans le **rechercher et remplacer** boîte de dialogue. Pour gérer ces situations, les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> pour gérer le processus de recherche du projet meilleures à ouvrir un document.

## <a name="see-also"></a>Voir aussi
- [Priorité de projet](../../extensibility/internals/project-priority.md)
- [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)