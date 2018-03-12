---
title: "Projets d’imbrication | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b91f9dc00b9130f2c239bd3254f78376bc0fdf3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="nesting-projects"></a>Projets d’imbrication
Les développeurs d’applications entreprise qui utilisent votre Package Visual Studio peuvent regrouper aisément des types de projets dans similaires [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’aide de *l’imbrication de projet*. Par exemple, le projet de modèle pour l’entreprise utilise des projets imbriqués pour grouper des projets en catégories. Projets de façade Business, l’interface utilisateur Web projets et ainsi de suite sont regroupés dans une catégorie.  
  
 Dans ce scénario, il n’existe aucune limite au nombre de projets, que le développeur peut imbriqués sous chaque projet parent, bien que le développeur peut fournir par programme des limites. Ce type de regroupement peut également être effectué récursive, auquel cas les projets du même type comme un projet enfant peuvent être imbriqués sous les enfants de devenir un sous-projet de l’enfant, qui est un sous-projet du parent.  
  
 Imbrication de projet n’est pas partie intégrante du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vous devez écrire le code pour activer l’imbrication et sous-projet imbrication dans des projets enfants. Le projet parent est un VSPackage spéciale, ou un type de projet, créé et inscrit avec son propre GUID qui inclut le code qui est requis pour implémenter l’imbrication de projet.  
  
 Vous trouverez un exemple de projets imbriqués dans l’exemple de projet de Example.Nested c#.  
  
## <a name="nested-projects-example"></a>Exemple de projets imbriqués  
 ![Imbriqué projets Solution](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Exemple de projets imbriqués  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : implémenter des projets imbriqués](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considérations pour décharger et recharger les projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [L’inscription des modèles de projet et élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Mise en œuvre de la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Le filtrage de la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)