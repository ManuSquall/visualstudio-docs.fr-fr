---
title: Stratégie de modèle et fenêtre Propriétés | Microsoft Docs
description: En savoir plus sur l’utilisation de la stratégie de modèle pour définir les valeurs par défaut des propriétés, masquer les propriétés et ajouter des propriétés dans le Fenêtre Propriétés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40f29eb5da5c8377c31a39a1e55868bf89f444a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898245"
---
# <a name="template-policy-and-the-properties-window"></a>Stratégie de modèle et fenêtre Propriétés
Lorsqu’un projet est contenu dans un projet de modèle d’entreprise, ce projet de modèle d’entreprise peut appliquer la stratégie. La stratégie de modèle devient un système de restriction qui peut être utilisé pour définir les valeurs par défaut des propriétés, masquer les propriétés, ajouter des propriétés, etc.

 L’utilisation de la stratégie de modèle pour contrôler l’affichage des informations dans la fenêtre **Propriétés** diffère de l’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> gère les propriétés d’objet au niveau du composant, tandis que la stratégie de modèle peut être utilisée pour contraindre les propriétés d’objet au niveau de la solution ou du projet. En d’autres termes

- Implémentez les méthodes sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> pour déterminer ce qui est affiché dans la fenêtre **Propriétés** pour des objets spécifiques

- Utiliser la stratégie de modèle au niveau de la solution et du projet pour déterminer ce qui est affiché dans la fenêtre **Propriétés** pour les objets spécifiés précédemment

  Utilisation d’une stratégie de modèle pour limiter de manière sélective des propriétés spécifiques dans la fenêtre **Propriétés** lorsqu’un élément de projet d’un type spécifié est sélectionné dans **Explorateur de solutions** peut être bénéfique pour tous les membres de l’équipe de développement qui travaillent sur un projet. Par exemple, à l’aide de la stratégie de modèle, vous pouvez configurer toutes les informations de chaîne de connexion dans une base de données pour vos développeurs et définir la chaîne de connexion en lecture seule. De cette façon, vous pouvez fournir un moyen simple pour garantir que chaque développeur utilise le chemin d’accès correct pour l’accès aux données.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
