---
title: Contexte du projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429936"
---
# <a name="project-context"></a>Contexte de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quand l’utilisateur ajoute ou travaille avec des projets et des éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer comment diverses opérations doivent être exécutées.  
  
 En règle générale, les fichiers sont les objets de projet standard que l’utilisateur crée explicitement en sélectionnant la commande **nouveau projet** ou rend disponible en sélectionnant la commande **ouvrir un projet** dans le menu **fichier** . Dans ces cas, les fichiers sont créés et ouverts dans le contexte d’un projet et le type de projet définit le contexte pour la modification du document.  
  
 Certains projets fournissent un contexte très riche. Par exemple, le projet gère une connexion de base de données à portée de projet, d’espace de noms de programmation ou de projet pour la liaison de données. L’utilisateur peut souvent ouvrir des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, tel qu’un élément de projet affiché dans Explorateur de solutions.  
  
 À d’autres moments, le contexte de projet d’un élément n’est pas explicitement spécifié. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant la commande **ouvrir un fichier existant** du menu **fichier** , lorsque le débogueur opère sur un fichier ou lorsque l’utilisateur clique sur la commande **Rechercher dans les fichiers** dans la boîte de dialogue **Rechercher et remplacer** . Pour gérer ces situations, l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> pour gérer le processus de recherche du meilleur projet pour ouvrir un document.  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité du projet](../../extensibility/internals/project-priority.md)   
 [Ajout d’un projet et de modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
