---
title: Stratégie de modèle et fenêtre des propriétés Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704665"
---
# <a name="template-policy-and-the-properties-window"></a>Stratégie de modèle et fenêtre Propriétés
Lorsqu’un projet est contenu à l’intérieur d’un projet de modèle d’entreprise, ce projet de modèle d’entreprise peut appliquer la politique. La stratégie de modèle devient un système de contrainte qui peut être employé pour définir des valeurs par défaut pour des propriétés, cacher des propriétés, ajouter des propriétés, et ainsi de suite.

 L’utilisation de la stratégie de modèle pour contrôler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>l’affichage des informations dans la fenêtre **propriétés** est différente de la mise en œuvre . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>gère les propriétés de l’objet au niveau des composants, tandis que la stratégie de modèle peut être utilisée pour limiter les propriétés des objets au niveau de la solution ou du projet. En d’autres termes,

- Implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> les méthodes pour déterminer ce qui est affiché dans la fenêtre **Propriétés** pour des objets spécifiques

- Utilisez la stratégie du modèle au niveau de la solution et du projet pour déterminer ce qui est affiché dans la fenêtre **Propriétés** pour les objets précédemment spécifiés

  L’utilisation de la stratégie de modèle pour limiter sélectivement les propriétés spécifiques dans la fenêtre **Propriétés** lorsqu’un élément de projet d’un type spécifié est sélectionné dans **Solution Explorer** peut être bénéfique pour tous les membres de l’équipe de développement travaillant sur un projet. Par exemple, en utilisant la stratégie de modèle, vous pouvez configurer toutes les informations de connexion-chaîne dans une base de données pour vos développeurs et faire la chaîne de connexion lue-seulement. De cette façon, vous pouvez fournir un moyen simple de s’assurer que chaque développeur utilise la voie correcte pour l’accès aux données.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
