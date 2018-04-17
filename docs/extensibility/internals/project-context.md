---
title: Contexte de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f52260d63088d7673322f3c42d43d00184a9af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="project-context"></a>Contexte du projet
Lorsque l’utilisateur ajoute ou fonctionne avec les projets et éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer la manière dont différentes opérations doivent être effectuées.  
  
 En règle générale, les fichiers sont les objets de projet standard que l’utilisateur crée explicitement en sélectionnant le **nouveau projet** commande ou mettent à disposition en sélectionnant le **ouvrir le projet** commande sur le  **Fichier** menu. Dans ces cas, les fichiers sont créés et ouvert dans le contexte d’un projet, et le type de projet définit le contexte de modification du document.  
  
 Certains projets fournissent un contexte très riche. Par exemple, le projet gère un espace de noms à portée de projet, par programme ou d’une connexion de base de données à portée de projet pour la liaison de données. L’utilisateur peut ouvrir fréquemment des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, comme un élément de projet affiché dans l’Explorateur de solutions.  
  
 À d’autres moments, le contexte d’un élément de projet n’est pas spécifié explicitement. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant le **ouvrir un fichier existant** commande sur le **fichier** menu, lorsque le débogueur fonctionne sur un fichier, ou lorsque l’utilisateur clique sur le **Rechercher dans les fichiers** dans les **rechercher et remplacer** boîte de dialogue. Pour gérer ces situations, les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> pour gérer le processus de recherche du projet meilleures pour ouvrir un document.  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité de projet](../../extensibility/internals/project-priority.md)   
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)