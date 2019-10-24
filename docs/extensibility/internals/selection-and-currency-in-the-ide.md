---
title: Sélection et devise dans l’IDE | Microsoft Docs
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
ms.openlocfilehash: edff400420ca5f0c93e1df85fb9118eee6302d02
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723966"
---
# <a name="selection-and-currency-in-the-ide"></a>Sélection et devise dans l’IDE
L’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gère les informations sur les objets actuellement sélectionnés par l’utilisateur à l’aide du *contexte*de sélection. Avec le contexte de sélection, les VSPackages peuvent participer au suivi des devises de deux manières :

- En diffusant les informations de devise relatives aux VSPackages dans l’IDE.

- En surveillant les sélections actuellement actives dans l’IDE.

## <a name="selection-context"></a>Contexte de sélection
 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effectue globalement le suivi de la devise IDE dans son propre objet de contexte de sélection globale. Le tableau suivant présente les éléments qui composent le contexte de sélection.

|Élément|Description|
|-------------|-----------------|
|Hiérarchie actuelle|En général, le projet actif ; une hiérarchie Active NULL indique que la solution dans son ensemble est actuelle.|
|ItemID actuel|Élément sélectionné dans la hiérarchie actuelle ; lorsqu’il existe plusieurs sélections dans une fenêtre de projet, il peut y avoir plusieurs éléments actuels.|
|`SelectionContainer` actuel|Contient un ou plusieurs objets pour lesquels le Fenêtre Propriétés doit afficher les propriétés.|

 En outre, l’environnement gère deux listes globales :

- Liste des identificateurs de commande d’interface utilisateur actifs

- Liste des types d’éléments actuellement actifs.

### <a name="window-types-and-selection"></a>Types de fenêtres et sélection
 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] organise Windows en deux types généraux :

- Fenêtres de type hiérarchie

- Fenêtres frames, telles que les fenêtres outil et document

  L’IDE effectue le suivi de la monnaie différemment pour chacun de ces types de fenêtres.

  La fenêtre de type de projet la plus courante est l’Explorateur de solutions, que l’IDE contrôle. Une fenêtre de type de projet effectue le suivi de la hiérarchie globale et de l’ItemID du contexte de sélection global, et la fenêtre s’appuie sur la sélection de l’utilisateur pour déterminer la hiérarchie actuelle. Pour les fenêtres de type de projet, l’environnement fournit le service global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, par l’intermédiaire duquel les VSPackages peuvent surveiller les valeurs actuelles des éléments ouverts. L’exploration des propriétés dans l’environnement est régie par ce service global.

  Les fenêtres Frame, en revanche, utilisent le DocObject dans la fenêtre frame pour envoyer la valeur SelectionContext (la hiérarchie/ItemID/SelectionContainer trio). . Les fenêtres Frame utilisent le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> à cet effet. DocObject peut envoyer uniquement des valeurs pour le conteneur de sélection, en laissant les valeurs locales de Hierarchy et ItemID inchangées, comme c’est généralement le cas pour les documents enfants MDI.

### <a name="events-and-currency"></a>Événements et devise
 Deux types d’événements peuvent se produire qui affectent la notion de devise de l’environnement :

- Événements qui sont propagés au niveau global et modifient le contexte de sélection du frame de fenêtre. Voici quelques exemples de ce type d’événement : ouverture d’une fenêtre enfant MDI, ouverture d’une fenêtre outil globale ou ouverture d’une fenêtre outil de type projet.

- Événements qui modifient les éléments suivis dans le contexte de sélection du frame de fenêtre. Les exemples incluent la modification de la sélection dans un DocObject ou la modification de la sélection dans une fenêtre de type projet.

## <a name="see-also"></a>Voir aussi
- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Commentaires à l’utilisateur](../../extensibility/internals/feedback-to-the-user.md)