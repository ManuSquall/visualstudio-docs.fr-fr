---
title: Imbriquer des projets | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2e05b47563c62f34e4a01c945a45d5c7ec069ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612229"
---
# <a name="nesting-projects"></a>Imbriquer des projets
Les développeurs d’applications entreprise qui utilisent votre Package VS peuvent regrouper facilement des types de projets dans similaires [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à l’aide de *l’imbrication de projet*. Par exemple, le projet de modèle pour l’entreprise utilise des projets imbriqués pour grouper des projets en catégories. Projets de façade Business, l’interface utilisateur Web projets et ainsi de suite sont regroupés dans une catégorie.

 Dans ce scénario, il n’existe aucune limite au nombre de projets, que le développeur peut imbriquer sous chaque projet parent, bien que le développeur peut fournir par programmation les limites. Ce type de regroupement peut également être effectué récursive, auquel cas les projets du même type comme un projet enfant peuvent être imbriqués sous l’enfant à devenir un sous-projet de l’enfant, qui est un sous-projet du parent.

 Imbrication de projet n’est pas partie intégrante du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vous devez écrire le code pour activer l’imbrication et un sous-projet imbrication dans des projets enfants. Le projet parent est un VSPackage spéciale, ou un type de projet, créé et inscrit avec son propre GUID qui inclut le code qui est requis pour implémenter l’imbrication de projet.

 Vous trouverez un exemple de projets imbriqués dans l’exemple de projet Example.Nested c#.

## <a name="nested-projects-example"></a>Exemple de projets imbriqués
 ![Imbriqué des projets Solution](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") exemple des projets imbriqués

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Implémenter des projets imbriqués](../../extensibility/internals/how-to-implement-nested-projects.md)
- [Considérations pour décharger et recharger des projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implémentation de la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrage de la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)