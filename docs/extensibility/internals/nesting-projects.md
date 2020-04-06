---
title: Projets de nidification (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707034"
---
# <a name="nesting-projects"></a>Imbriquer des projets
Les développeurs d’applications d’entreprise qui utilisent votre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] forfait VS peuvent commodément regrouper des types similaires de projets en utilisant *la nidification du projet.* Par exemple, le projet Enterprise Template utilise des projets imbriqués pour regrouper des projets en catégories. Les projets de façade d’entreprise, les projets d’interface utilisateur Web, etc. sont regroupés dans une catégorie.

 Dans ce scénario, il n’y a pas de limite au nombre de projets que le promoteur peut imbriquer dans le cadre de chaque projet parent, bien que le promoteur puisse fournir des limites programmatiques. Ce type de regroupement peut également être rendu récursif, auquel cas les projets du même type qu’un projet d’enfant peuvent être imbriqués sous l’enfant pour devenir un sous-projet de l’enfant, qui est un sous-projet du parent.

 La nidification du projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]n’est pas une partie intrinsèque de . Vous devez écrire le code pour permettre la nidification et la nidification sous-projet dans les projets pour enfants. Le projet parent est un VSPackage spécial, ou type de projet, créé et enregistré avec son propre GUID qui comprend le code qui est nécessaire pour implémenter la nidification du projet.

 Vous pouvez trouver un exemple sur la façon de nicher des projets dans le [Comment mettre en œuvre des projets imbriqués](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Exemple de projets imbriqués
 ![Solution de projets imbriqués](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjets") Exemple de projets imbriqués

## <a name="see-also"></a>Voir aussi
- [Considérations pour décharger et recharger des projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implémentation de la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrage de la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Paramètres contextuelles](../../extensibility/internals/context-parameters.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
