---
title: Imbrication de projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180413"
---
# <a name="nesting-projects"></a>Imbriquer des projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les développeurs d’applications d’entreprise qui utilisent votre package VS peuvent facilement regrouper des types similaires de projets dans à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’aide de l' *imbrication de projet*. Par exemple, le projet de modèle d’entreprise utilise des projets imbriqués pour regrouper des projets en catégories. Les projets de façade métier, les projets d’interface utilisateur Web, etc., sont regroupés dans une même catégorie.  
  
 Dans ce scénario, il n’existe aucune limite au nombre de projets que le développeur peut imbriquer sous chaque projet parent, même si le développeur peut fournir des limites par programmation. Ce type de regroupement peut également être récursif. dans ce cas, les projets du même type qu’un projet enfant peuvent être imbriqués sous l’enfant pour devenir un sous-projet de l’enfant, qui est un sous-projet du parent.  
  
 L’imbrication de projets n’est pas une partie intrinsèque de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Vous devez écrire le code pour activer l’imbrication et l’imbrication de sous-projets dans les projets enfants. Le projet parent est un VSPackage spécial, ou type de projet, créé et inscrit avec son propre GUID, qui comprend le code requis pour implémenter l’imbrication de projet.  
  
 Vous trouverez un exemple de projets imbriqués dans l’exemple de projet imbriqué C#.  
  
## <a name="nested-projects-example"></a>Exemple de projets imbriqués  
 ![Solution de projets imbriqués](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Exemple de projets imbriqués  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : implémenter des projets imbriqués](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considérations sur le déchargement et le rechargement des projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implémentation de la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrage de la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
