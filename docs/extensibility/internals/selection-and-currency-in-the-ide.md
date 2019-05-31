---
title: Sélection et la devise dans l’IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23ce55a85fd6f1408c623a49fc16b8766c535dfc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318698"
---
# <a name="selection-and-currency-in-the-ide"></a>Sélection et devise dans l’IDE
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tient à jour l’environnement de développement intégré (IDE) plus d’informations sur les utilisateurs les objets actuellement sélectionnés à l’aide de sélection *contexte*. Avec le contexte de sélection, les VSPackages peuvent prendre part à monétaire suivi de deux manières :

- En propageant les informations de devise sur les VSPackages à l’IDE.

- En surveillant les sélections des utilisateurs actuellement actifs dans l’IDE.

## <a name="selection-context"></a>Contexte de sélection
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalement effectue le suivi de devise IDE dans son propre objet de contexte de sélection globale. Le tableau suivant présente les éléments qui composent le contexte de sélection.

|Élément|Description|
|-------------|-----------------|
|Hiérarchie actuelle|En général, le projet actuel. une hiérarchie en cours de valeur NULL indique que la solution dans son ensemble est en cours.|
|ItemID actuel|L’élément sélectionné dans la hiérarchie actuelle ; Lorsqu’il existe plusieurs sélections dans une fenêtre de projet, il peut y avoir plusieurs éléments en cours.|
|Actuel `SelectionContainer`|Contient l’un ou plusieurs objets pour lequel la fenêtre de propriétés doit afficher les propriétés.|

 En outre, l’environnement gère deux listes globales :

- Une liste d’identificateurs de commande actives l’interface utilisateur

- Liste des types d’éléments actuellement active.

### <a name="window-types-and-selection"></a>Sélection et les Types de fenêtres
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organise windows en deux types généraux :

- Windows de type de hiérarchie

- Fenêtres frame, telles que des fenêtres Outil et document

  L’IDE effectue le suivi de devise différemment pour chacun de ces types de fenêtre.

  La fenêtre de type de projet plus courantes est l’Explorateur de solutions, qui contrôle l’IDE. Une fenêtre de type de projet effectue le suivi de la hiérarchie globale et ItemID du contexte de sélection globale, et la fenêtre s’appuie sur la sélection d’utilisateur pour déterminer la hiérarchie actuelle. Pour windows de type de projet, l’environnement fournit le service global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, via lesquelles VSPackages peuvent surveiller les valeurs actuelles des éléments ouverts. Propriété de navigation dans l’environnement est pilotée par ce service global.

  Fenêtres frame, utilisent quant à eux, sera imprimé dans la fenêtre frame pour transmettre la valeur SelectionContext (le trio hiérarchie/ItemID/SelectionContainer). . Fenêtres frame utilisent le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> à cet effet. Le DocObject peut transmettre uniquement les valeurs pour le conteneur de sélection, en laissant les valeurs locales pour la hiérarchie et ItemID inchangés, comme cela est courant pour les documents enfants MDI.

### <a name="events-and-currency"></a>Événements et devise
 Deux types d’événements peuvent se produire et affectent la notion de l’environnement de devise :

- Événements qui sont propagées jusqu’au niveau global et de modifier le contexte de sélection de fenêtre frame. Exemples de ce type d’événement incluent une fenêtre enfant MDI en cours d’ouverture d’une fenêtre outil global en cours d’ouverture ou une fenêtre d’outil de type de projet en cours d’ouverture.

- Événements qui modifient les éléments suivis dans le contexte de sélection de fenêtre frame. Exemples incluent la modification de sélection au sein d’un DocObject ou la modification de sélection dans une fenêtre de type de projet.

## <a name="see-also"></a>Voir aussi
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)