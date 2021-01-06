---
title: Imbrication de projets | Microsoft Docs
description: En savoir plus sur l’imbrication de projets, qui permet aux développeurs d’applications qui utilisent votre VSPackage de regrouper des types de projets similaires dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 464538d7f7be68737715cb6fd10fda4017a5556a
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876660"
---
# <a name="nesting-projects"></a>Imbriquer des projets
Les développeurs d’applications d’entreprise qui utilisent votre package VS peuvent facilement regrouper des types similaires de projets dans à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’aide de l' *imbrication de projet*. Par exemple, le projet de modèle d’entreprise utilise des projets imbriqués pour regrouper des projets en catégories. Les projets de façade métier, les projets d’interface utilisateur Web, etc., sont regroupés dans une même catégorie.

 Dans ce scénario, il n’existe aucune limite au nombre de projets que le développeur peut imbriquer sous chaque projet parent, même si le développeur peut fournir des limites par programmation. Ce type de regroupement peut également être récursif. dans ce cas, les projets du même type qu’un projet enfant peuvent être imbriqués sous l’enfant pour devenir un sous-projet de l’enfant, qui est un sous-projet du parent.

 L’imbrication de projets n’est pas une partie intrinsèque de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Vous devez écrire le code pour activer l’imbrication et l’imbrication de sous-projets dans les projets enfants. Le projet parent est un VSPackage spécial, ou type de projet, créé et inscrit avec son propre GUID, qui comprend le code requis pour implémenter l’imbrication de projet.

 Vous trouverez un exemple sur la façon d’imbriquer des projets dans la rubrique [Comment : implémenter des projets imbriqués](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Exemple de projets imbriqués
 ![Solution de projets imbriqués](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Exemple de projets imbriqués

## <a name="see-also"></a>Voir aussi
- [Considérations pour décharger et recharger des projets imbriqués](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Prise en charge de l’Assistant pour les projets imbriqués](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implémentation de la gestion des commandes pour les projets imbriqués](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrage de la boîte de dialogue AddItem pour les projets imbriqués](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
