---
title: Stratégie de modèle et fenêtre Propriétés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7135a7c99f1566eaacb4079e9787cf2b5606682
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722690"
---
# <a name="template-policy-and-the-properties-window"></a>Stratégie de modèle et fenêtre Propriétés
Lorsqu’un projet est contenu dans un projet de modèle d’entreprise, ce projet de modèle d’entreprise peut appliquer la stratégie. La stratégie de modèle devient un système de restriction qui peut être utilisé pour définir les valeurs par défaut des propriétés, masquer les propriétés, ajouter des propriétés, etc.

 L’utilisation de la stratégie de modèle pour contrôler l’affichage des informations dans la fenêtre **Propriétés** est différente de l’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gère les propriétés de l’objet au niveau du composant, tandis que la stratégie de modèle peut être utilisée pour contraindre les propriétés de l’objet au niveau de la solution ou du projet. En d’autres termes

- Implémentez les méthodes sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> pour déterminer ce qui est affiché dans la fenêtre **Propriétés** pour des objets spécifiques

- Utiliser la stratégie de modèle au niveau de la solution et du projet pour déterminer ce qui est affiché dans la fenêtre **Propriétés** pour les objets spécifiés précédemment

  Utilisation d’une stratégie de modèle pour limiter de manière sélective des propriétés spécifiques dans la fenêtre **Propriétés** lorsqu’un élément de projet d’un type spécifié est sélectionné dans **Explorateur de solutions** peut être bénéfique pour tous les membres de l’équipe de développement qui travaillent sur un projet. Par exemple, à l’aide de la stratégie de modèle, vous pouvez configurer toutes les informations de chaîne de connexion dans une base de données pour vos développeurs et définir la chaîne de connexion en lecture seule. De cette façon, vous pouvez fournir un moyen simple pour garantir que chaque développeur utilise le chemin d’accès correct pour l’accès aux données.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)