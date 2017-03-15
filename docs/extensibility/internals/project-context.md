---
title: Contexte de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>Contexte du projet
Lorsque l’utilisateur ajoute ou fonctionne avec les projets et éléments de projet, l’IDE utilise la notion de contexte de projet pour déterminer comment diverses opérations doivent être effectuées.  
  
 En règle générale, les fichiers sont les objets de projet standard que l’utilisateur crée explicitement en sélectionnant le **nouveau projet** commande ou met à disposition en sélectionnant le **ouvrir un projet** sur la **fichier** menu. Dans ce cas, les fichiers sont créés et ouvert dans le contexte d’un projet et le type de projet définit le contexte d’édition du document.  
  
 Certains projets fournissent un contexte très riche. Par exemple, le projet gère l’espace de noms à portée de projet, par programmation ou connexion à portée de projet de base de données pour la liaison de données. L’utilisateur peut ouvrir fréquemment des fichiers ou des connexions de base de données directement à l’aide d’un objet de projet particulier, comme un élément de projet affiché dans l’Explorateur de solutions.  
  
 À d’autres moments, le contexte d’un élément de projet n’est pas spécifié explicitement. Par exemple, le contexte d’un élément n’est pas disponible lorsque l’utilisateur ouvre un fichier en sélectionnant le **ouvrir un fichier existant** sur le **fichier** menu, lorsque le débogueur fonctionne sur un fichier, ou lorsque l’utilisateur clique sur le **rechercher dans les fichiers** commande le **rechercher et remplacer** boîte de dialogue. Pour gérer ces situations, les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>pour gérer le processus de recherche du projet pour ouvrir un document meilleures.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>  
  
## <a name="see-also"></a>Voir aussi  
 [Priorité du projet](../../extensibility/internals/project-priority.md)   
 [Ajout de projet et modèles d’élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)
