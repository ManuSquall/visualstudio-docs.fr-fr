---
title: Extension des propriétés (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708420"
---
# <a name="extend-properties"></a>Étendre les propriétés
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fenêtre **Propriétés** est un navigateur de propriété universel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour les composants COM et COM et prend en charge tous les produits. La fenêtre **Propriétés** fonctionne avec `ITypeInfo` des informations de type et des métadonnées COMMD pour répertorier les propriétés de conception-temps pour l’objet actuellement sélectionné dans n’importe quelle autre fenêtre dans l’environnement de développement intégré (IDE).

 La fenêtre **Propriétés,** qui peut être ouverte en appuyant sur **F4** sur le clavier, ou en sélectionnant **Properties Window** sur le menu **View,** est utilisée pour afficher et modifier les propriétés et les événements de configuration indépendants, de conception-temps d’objets sélectionnés. Les propriétés dépendantes de la configuration, associées aux solutions et aux projets, sont affichées sur [les pages Propriété.](../../extensibility/internals/property-pages.md) Pour plus d’informations, [Gérer les options de configuration](../../extensibility/internals/managing-configuration-options.md).

 ![Aperçu de fenêtre de propriétés](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Fenêtre de propriétés

 Cette section fournit des informations détaillées qui se rapportent aux zones individuelles de la fenêtre **Propriétés** et aux interfaces que vous devez implémenter et appeler pour remplir la fenêtre.

## <a name="in-this-section"></a>Contenu de cette section
- [Aperçu de fenêtre de propriétés](../../extensibility/internals/properties-window-overview.md)

 Explique le but de la fenêtre **Propriétés** par rapport à la fenêtre d’outil et la fenêtre de document.

- [Stratégie de modèle et fenêtre propriétés](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Discute de la façon dont un projet est contenu dans un projet de modèle d’entreprise et de la façon dont ce projet de modèle d’entreprise peut appliquer la politique.

- [Propriétés champs de fenêtre et interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Explique la base de sélection qui détermine quelles informations sont affichées dans la fenêtre **Propriétés.**

- [Liste d’objets de fenêtre de propriétés](../../extensibility/internals/properties-window-object-list.md)

 Décrit le but de la liste des objets de fenêtre **Propriétés,** décrivant comment, lorsqu’un objet différent de cette liste déclenche un appel, l’environnement est informé qu’un nouvel objet a été sélectionné.

- [Boutons de fenêtre de propriétés](../../extensibility/internals/properties-window-buttons.md)

 Explique le but des quatre boutons par défaut affichés sur la barre d’outils de fenêtre **Propriétés.**

- [Grille d’affichage des propriétés](../../extensibility/internals/properties-display-grid.md)

 Explique où les noms de propriété et les champs de valeurs de propriété se trouvent dans le réseau.

## <a name="related-sections"></a>Sections connexes
- [Types de projet](../../extensibility/internals/project-types.md)

 Discute des projets comme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les éléments constitutifs de l’IDE.

- [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)

 Décrit comment vous pouvez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliser la plate-forme pour tester et débogage en continu les applications au fur et à mesure que vous les construisez.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Décrit l’interface, `IDispatch` qui a d’abord été conçu pour soutenir l’automatisation, fournissant un mécanisme lié en retard pour accéder et récupérer des informations sur les méthodes et les propriétés d’un objet.

- [Gérer les paramètres d’application (.NET)](../../ide/managing-application-settings-dotnet.md)

 Fournit un aperçu des paramètres d’application qui vous permettent de configurer votre application afin que les valeurs de propriété soient stockées dans un fichier de configuration externe au lieu du code compilé de l’application.

- [Solutions et projets](../../ide/solutions-and-projects-in-visual-studio.md)

 Explique [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comment gère efficacement les éléments tels que les références, les connexions de données, les dossiers et les fichiers qui sont requis par votre effort de développement grâce à des solutions et des projets.

- [Étendre d’autres parties de Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Explique comment utiliser les services de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour créer des éléments d’interface utilisateur qui correspondent au reste de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
